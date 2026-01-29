<template>
  <div>
    <h1>Get All Menus</h1>
    <div v-if="menus.length">
      <h4>จำนวนเมนู {{ menus.length }}</h4>
      <div v-for="menu in menus" v-bind:key="menu.id">
        <p>ID : {{ menu.id }}</p>
        <p>Name - type : {{ menu.name }} {{ menu.type }}</p>
        <p>price : {{ menu.price }}</p>
        <p>
          <button v-on:click="navigateTo('/menu/' + menu.id)">ดูข้อมูลเมนู</button><hr>
          <button v-on:click="navigateTo('/menu/edit/' + menu.id)">แก้ไขข้อมูล</button><hr>
          <button v-on:click="deleteMenu(menu)">ลบข้อมูล</button>
        </p>
        <hr />
      </div>
    </div>

    <p><button @click="navigateTo('/menu/create')">สร้างเมนู</button></p>
  </div>
</template>

<script>
import MenusService from '../../services/MenusService'
export default {
  methods: {
    navigateTo(route) {
      this.$router.push(route)
    },
    async deleteMenu(menu) {
      let result = confirm("Want to delete?")
      if (result) {
        try {
          await MenusService.delete(menu)
          this.refreshData()
        } catch (err) {
          console.log(err)
        }
      }
    },
    async refreshData() {
      this.menus = (await MenusService.index()).data
    }
  },

  data() {
    return {
      menus: []
    }
  },

  async created() {
    try {
      this.menus = (await MenusService.index()).data
      console.log(this.menus)
    } catch (error) {
      console.log(error)
    }
  }
}
</script>

<style scoped>
/* CSS เฉพาะหน้านี้ */
</style>
