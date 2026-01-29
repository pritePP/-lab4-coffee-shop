<template>
    <div>
        <h1>Create Menu</h1>
        <form v-on:submit.prevent="createMenu">
            <p>Coffee name: <input type="text" v-model="coffee.name"></p>
            <p>coffee type: <input type="text" v-model="coffee.type"></p>
            <p>price: <input type="text" v-model="coffee.price"></p>
            <p>Id: <input type="text" v-model="coffee.Id"></p>
            <p><button type="submit">Create Coffee Menu<</button></p>
        </form>
    </div>
</template>

<script>
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
        async createMenu() {
            try {
                awaitMenuService.post(this.menu)
                this.$router.push({
                    name: 'menus'
                })
            } catch (err) {
                console.log(err)
            }
        }
    }
}
</script>

<style scoped>
/* CSS เฉพาะหน้านี้ */
</style>