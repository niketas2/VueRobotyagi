<template>
	<!-- <from>
		<div class="buttons">
			<button @click="addLike" class="likes">Лайк</button>
			<button @click="addDislike" class="dislikes">Дизлайк</button>
		</div>
		<p class="likes">Кол-во лайков: {{ likes }}</p>
		<p class="dis">Кол-во дизлайков {{ dislikes }}</p>
	</from> -->
	<div class="app">
		<form @submit.prevent>
		<p class="create">Создание поста</p>
		<input 
		v-bind:value='title'
		@input='inputTitle'
		class='input' type="text" 
		placeholder="Название">
	</input>
	<input 
		v-bind:value='description'
		@input='inputDescription'
		class='input' type="text" 
		placeholder="Описание">
	</input>
		<button @click='createPost' class="addButton">Добавить</button>
	</form>
	<div class="post" v-for="post in posts">
		<div><strong>Название: </strong>{{ post.title }}</div>
		<div><strong>Описание: </strong>{{ post.description }}</div>
	</div>

</div>
</template>
<script>
export default {
	data() {
		return {
			posts: [
			],
			title: "",
			description: "",
		}
	},
	methods: {
		createPost() {
			const newPost = {
				id: Date.now(),
				title: this.title,
				description: this.description
			}
			this.posts.push(newPost)
			this.title = '',
			this.description = ''
		},
		inputTitle(event) {
		this.title = event.target.value
		},
		inputDescription(event) {
		this.description = event.target.value
		},
	},
}
// export default {
// 	data() {
// 		return {
// 			likes: 0,
// 			dislikes: 0,
// 		}
// 	},
// 	methods: {
// 		addLike() {
// 			this.likes += 1
// 		},
// 		addDislike() {
// 			this.dislikes += 1
// 		},
// 	},
// }
</script>

<style>
* {
	background-color: #3f3f3f;
	padding: 0;
	margin: 0;
	box-sizing: border-box;
	color: #ffffff;
}
.app{
	padding: 50px;
}
.post {
	margin-top: 15px;
	padding: 15px;
	border: 2px solid teal;
}
.input{
	width: 100%;
	border: 2px solid teal;
	padding: 10px;
	margin-top: 10px;
}
form{
	display: flex;
	flex-direction: column;
}
.addButton{
	align-self: flex-end;
	margin-top: 10px;
	padding: 15px;
	border-radius: 10px;
	color: #fff;
	border: 2px solid teal;
	cursor: pointer;
}
</style>
