<template>
	<div class="test">
		<input type="text" v-model="title"><br />
		<h1>{{title}}</h1>
		<p>{{user.firstName}}</p>
		<p v-text="user.firstName"></p>
		{{titleHtml}}
		<p v-html="titleHtml"></p>
		<p v-if="showNameTrue">{{user.firstName}}</p>
		<p v-if="showNameFalse">{{user.firstName}}</p>
		<p v-else>Nobody</p>
		<ul>
			<li v-for="item in items">{{item.title}}</li>
		</ul>
		<button v-on:click="greet('Hello World')">Say Greeting</button><br />
		<input type="text" v-on:keyup="pressKey" v-on:keyup.enter="enterHit">
		<hr />
		<label>First Name: </label><input type="text" v-model="user.firstName">
		<label>Last Name: </label><input type="text" v-model="user.lastName">
		<h3>{{fullname}}</h3>
		<hr />
		<h2>props message</h2>
		<p>{{propNumber}}</p>
		<p>{{propE}}</p>
		<p>{{propF}}</p>
	</div>
</template>

<script>
	export default {
		name: 'test',
		props: {
		    propNumber: {
		      type: Number,
		      default: 100
		    },
		    // object/array defaults should be returned from a
		    // factory function
		    propE: {
		      type: Object,
		      default: function () {
		        return {
		        	typeMessage: 'success',
		        	text: 'insert success'
		        }
		      }
		    },
		    // custom validator function
		    propF: {
		      validator: function (value) {
		        return value > 10
		      }
		    }
		},
		data() {
			return {
				title: 'Hello world',
				user: {
					firstName: 'John',
					lastName: 'Doe'
				},
				showNameTrue: true,
				showNameFalse: false,
				titleHtml: '<h1>Hello World HTML</h1>',
				items: [
					{title: 'Item One'},
					{title: 'Item Two'},
					{title: 'Item Three'}
				]
			}
		},
		methods: {
			greet: function(greeting){
				alert(greeting);
			},
			pressKey: function(e){
				console.log(e.target.value);
			},
			enterHit: function(){
				console.log('You Hit Enter');
			}
		},
		computed: {
			fullname: function(){
				return this.user.firstName+ ' ' +this.user.lastName;
			}
		}
	}
</script>

<style scoped>

</style>