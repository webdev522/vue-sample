<template>
    <div class="users">
        <h1>Users</h1>
        <form v-on:submit="addUser">
            <input type="text" v-model="newuser.name" placeholder="enter name">
            <br />
            <input type="text" v-model="newuser.email" placeholder="enter email">
            <br />
            <input type="submit" value="Submit">

        </form>
        <ul>
            <li v-for="user in users">
                <!--{{ user.name }}-->
                <input type="checkbox" class="toggle" v-model="user.contacted">
                <span :class="{contacted: user.contacted}">
                    {{user.name}}: {{user.email}}
                </span>
                <button v-on:click="deleteUser(user)">x</button>
            </li>
        </ul>
    </div>
</template>

<script>
export default {
    name: 'users',
    data() {
        return {
            newuser: {},
            users: [
                // {
                //     name: 'John Doe',
                //     email: 'johndoe@gmail.com',
                //     contacted: false
                // },
                // {
                //     name: 'Kohn Doe',
                //     email: 'Kohndoe@gmail.com',
                //     contacted: true
                // },
                // {
                //     name: 'Aohn Doe',
                //     email: 'Aohndoe@gmail.com',
                //     contacted: false
                // }
            ]
        }
    },
    methods: {
        addUser: function(e) {
            // console.log('add');
            this.users.push({
                name: this.newuser.name,
                email: this.newuser.email,
                contacted: false
            });
            e.preventDefault();
        },
        deleteUser: function(user) {
            this.users.splice(this.users.indexOf(user), 1);
        }
    },
    created: function() {
        console.log('created ran...')
        this.$http.get('https://jsonplaceholder.typicode.com/users')
            .then(function(response) {
                this.users = response.data
            })
    }
}
</script>

<style scoped>
.contacted {
    text-decoration: line-through;
}
</style>