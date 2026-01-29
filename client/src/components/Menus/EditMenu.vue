<template>
    <div>
        <h1>Edit Menu</h1>
        <form v-on:submit.prevent="editUser">
          <p>Coffee name: <input type="text" v-model="coffee.name"></p>
            <p>coffee type: <input type="text" v-model="coffee.type"></p>
            <p>price: <input type="text" v-model="coffee.price"></p>
            <p>Id: <input type="text" v-model="coffee.Id"></p>
            <p><button type="submit">Edit Coffee Menu<</button></p>
        </form>
    </div>
</template>

<script>
import MenusService from '../../services/MenusService';
import UsersService from '../../services/MenusService'
export default {
    data() {
        return {
            Menu: {
                Coffeename: '',
                coffeetype: '',
                price: '',
                Id: '',
                status: 'active'
            }
        }
    },
    methods: {
        async editMenu() {
            try {
                await MenusService.put(this.menu)
                this.$router.push({
                    name: 'menus'
                })
            } catch (err) {
                console.log(err)
            }
        }
    },
    async created() {
        try {
            let menuId = this.$route.params.userId
            this.menu = (await MenusService.show(menuId)).data
        } catch (error) {
            console.log(error)
        }
    }

}
</script>

<style scoped>
/* CSS เฉพาะหน้านี้ */
</style>