<template>
	<div id="app">
		<Header />
		<Todos :todos="todos" v-on:del-todo="deleteTodo" />
	</div>
</template>

<script>
import Todos from "./components/Todos/Todos";
import Header from "./components/layout/Header";

export default {
	name: "App",
	components: {
		Todos,
		Header,
	},
	data() {
		return {
			todos: [
				{
					id: 1,
					title: "Todo One",
					completed: false,
				},
				{
					id: 2,
					title: "Todo Two",
					completed: true,
				},
				{
					id: 3,
					title: "Todo Three",
					completed: false,
				},
			],
		};
	},
	methods: {
		deleteTodo(id) {
			this.todos = this.todos.filter(
				(todo) => todo.id !== id
			);
		},
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
img {
	display: block;
}
</style>
