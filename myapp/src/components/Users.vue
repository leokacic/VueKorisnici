<template>
	<div class="users">
        <h1> Users </h1>
        <form v-on:submit="addUser">
        <input type="text" v-model="newUser.name" placeholder="Enter name">
        <br />
        <input type="text" v-model="newUser.email" placeholder="Enter email">
        <br />
        <input type="submit" value="Submit">
        </form>
        <ul>
            <li v-for="user in users" :key="user.email">
                <input type="checkbox" class="toggle" v-model="user.contacted">
            <span :class="{contacted: user.contacted}"> 
            {{user.name}}: {{user.email}}
            </span>
            <button v-on:click="deleteUser(user)"> x </button>
            </li>
        </ul>
	</div>
</template>

	<script>
		export default {
		name: 'users',

		data(){
			return {
                newUser: {},
                users:[
                   
                ]
				
				}
			},

		methods:{
			addUser: function(e){
                this.users.push({
                    name: this.newUser.name,
                    email: this.newUser.email,
                    contacted: false
                });
                e.preventDefault();           
            },
            deleteUser: function(user){
                this.users.splice(this.users.indexOf(user),1);
            }
            },
            editUser: function(user){
                this.users.edit();
            },
            created: function(){
                this.$http.get('https://jsonplaceholder.typicode.com/users')
                .then(function(response){
                   this.users=response.data;

                });
            }	
		}
	</script>

	<style scoped>
        .contacted{
            text-decoration: line-through;
        }
	</style>
