<template>
    <div class="test">
        <h1>{{title}}</h1>
        <input type="text" v-model="title">
        <br />
        <p v-if="showname">{{user.firstname}} </p>
        <p v-else="showname">nobody</p>
        <!--<p v-text="user.firstname"></p>-->
        <ul>
            <li v-for="item in items">{{item.title}}</li>
        </ul>
        <button v-on:click="greet('Hello World')">Say Greeting</button>
        <br />
        <input type="text" v-on:keyup="pressKey" v-on:keyup.enter="pressEnter">
        <hr />
        <label>First Name: </label><input type="text" v-model="user.firstname">
        <br />
        <label>Last Name: </label><input type="text" v-model="user.lastname">
        <br />
        <h3>{{fullname}}</h3>
        <h2>{{msg}}</h2>
    </div>
</template>

<script>
export default {
    name: 'test',
    props: {
        msg: {
            type: String,
            default: 'Foobar'
        }
    },
    data() {
        return {
            title: 'Hello World',
            user: {
                firstname: 'John',
                lastname: 'Doe'
            },
            showname: true,
            items: [
                {title: 'item 1'},
                {title: 'item 2'},
                {title: 'item 3'}
            ]
        }
    },
    methods: {
        greet: function(greeting) {
            alert(greeting);
        },
        pressKey: function(e) {
            console.log(e.target.value);
        },
        pressEnter: function(e) {
            console.log(e.target.value);
        }
    },
    computed: {
        fullname: function() {
            return this.user.firstname + ' ' + this.user.lastname;
        }
    }
   
}
</script>

<style scoped>

</style>