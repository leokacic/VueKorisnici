<template>
	<div class="test">
		<input type="text" v-model="title"><br/>
	<h1> {{title}} </h1>
	<p v-if="showName" >{{user.firstName}} </p>
	<p v-else>Nobody</p>
	<ul>
		<li v-for="item in items" :key="item.id"> {{item.title}} 
		</li>
	</ul>
	<button v-on:click="greet('Hello world')">Say greeting</button><br>
	<br /> 
	<input type="text" v-on:keyup="pressKey" v-on:keyup.enter="enterHit">
	<hr />
	<lable> First name: </lable><input type="text" v-model="user.firstName"><br/>
	<h1> {{user.firstName}} </h1>
	<label> Last name: </label><input type="text" v-model="user.lastName"><br/>
	<h1> {{user.lastName}} </h1>
	<br />
	<h3>{{fullName}}</h3>
	<h2>{{msg}} </h2>
	</div>
</template>

	<script>
		export default {
		name: 'test',
		props:{
			msg:{
				type: String,
				default:'Foobar'
			}
		},
		data(){
			return {
				title:'Hello world',
				brojMobitela: 5,
				user: {
					firstName: 'John',
					lastName:'Doe'
					},
				showName:true,
				items: [
					{title:'item one',
					id:1},
					{title: 'item two',
					id:2},
					{title: 'item three',
					id:3}
				]

				}
			},

		methods:{
			greet: function(greeting){
				alert(greeting);
			},
			pressKey: function(e){
				console.log(e.target.value);
			},
			enterHit: function(){
				console.log("You hit enter");
			},
			
				
			},	

		computed: {
				fullName: function(){
					return this.user.firstName +' ' +this.user.lastName;
				}
			}
		}
	</script>

	<style scoped>

	</style>
