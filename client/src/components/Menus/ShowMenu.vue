<template>
  <div>
    <h1>Show Menu</h1>
    <div v-if="user">
      <p>ID : {{ this.menu.id }}</p>
      <p>name - type : {{ this.menu.name }} {{ this.menu.type }}</p>
      <p>price : {{ this.menu.price }}</p>
    </div>
  </div>
</template>

<script>
import MenusService from '../../services/MenusService'
export default {
  data() {
    return {
      menu: null
    }
  },
  created() {
    console.log("created menuId:", this.menu)
  },
  async mounted() {
    var menuId = this.$route.params.menuId
    this.menu = (await MenusService.show(menuId)).data
    console.log("mounted menuId:", this.menu)
  }

}
</script>

<style scoped>
/* CSS เฉพาะหน้านี้ */
</style>
