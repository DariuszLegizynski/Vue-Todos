<template>
	<div>
		<form @submit="addTodo">
			<input
				type="text"
				v-model="title"
				name="title"
				placeholder="Adda a Todo..."
			/>
			<input type="submit" value="Submit" class="btn" />
		</form>
	</div>
</template>

<script>
import uuid from "uuid";
export default {
	name: "AddTodo",
	data() {
		return {
			title: "",
		};
	},
	methods: {
		addTodo(e) {
			e.preventDefault();
			const newTodo = {
				id: uuid.v4(),
				title: this.title,
				completed: false,
			};
			//send up to parent
			this.$emit("add-todo", newTodo);

			this.title = "";
		},
	},
};
</script>

<style src="./AddTodo.css" scoped></style>
