<template>
	<div id="app">
		<Header />
		<AddTodo v-on:add-todo="addTodo" />
		<Todos :todos="todos" v-on:del-todo="deleteTodo" />
	</div>
</template>

<script>
import Header from "./components/layout/Header";
import Todos from "./components/Todos/Todos";
import AddTodo from "./components/addTodo/AddTodo";

export default {
	name: "App",
	components: {
		Todos,
		Header,
		AddTodo,
	},
	data() {
		return {
			todos: [],
		};
	},
	methods: {
		deleteTodo(id) {
			this.todos = this.todos.filter(
				(todo) => todo.id !== id
			);
		},
		addTodo(newTodo) {
			this.todos = [...this.todos, newTodo];
		},
	},
	async mounted() {
		const response = await fetch(
			"https://jsonplaceholder.typicode.com/todos?_limit=10"
		).catch((err) => alert(err.message));
		const fetchedData = await response
			.json()
			.catch((err) => alert(err.message));
		this.todos = fetchedData;
	},
};
</script>

<style>
* {
	box-sizing: border-box;
	margin: 0;
	padding: 0;
	scroll-behavior: smooth;
}
body {
	font-family: Arial, Helvetica, sans-serif;
	line-height: 1.4;
}
.btn {
	display: inline-block;
	border: none;
	background: #555;
	color: #fff;
	padding: 7px 20px;
	cursor: pointer;
}
.btn:hover {
	background: #666;
}
img {
	display: block;
}
</style>
