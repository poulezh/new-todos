<template>
	<div class="app">
		<h2>Page of Posts</h2>
		<div class="app__btns">
			<MyButton class="create__btn" @click="showDialog">Create Posts</MyButton>
			<MySelect 
				v-model="selectedSort"
				:options="sorpOptions"
			></MySelect>
		</div>
		<!-- <input type="text" v-model.trim="modificatorValue"> -->
		<MyModalDialog v-model:show="dialogVisible">
			<PostForm @create="createPost"></PostForm>
		</MyModalDialog>
		<PostList :posts="posts" @remove="removePost" v-if="!isPostLoading"></PostList>
		<div v-else class="loading"></div>
	</div>
</template>

<script>
import PostForm from "@/components/PostForm.vue";
import PostList from "@/components/PostList.vue";
import MyButton from "@/components/UI/MyButton.vue";
import axios from "axios";
import MySelect from "./components/UI/MySelect.vue";
export default {
	components: {
    PostForm,
    PostList,
    MyButton,
    MyButton,
    MySelect
},
	data() {
		return {
			posts: [],
			dialogVisible: false,
			modificatorValue: "",
			isPostLoading: false,
			selectedSort: '',
			sorpOptions: [
				{value: 'title', name: 'name'},
				{value: 'body', name: 'description'},
			]
		};
	},
	methods: {
		createPost(post) {
			this.posts.push(post);
			this.dialogVisible = false;
		},
		removePost(post) {
			this.posts = this.posts.filter((p) => p.id !== post.id);
		},
		showDialog() {
			this.dialogVisible = true;
		},
		async fetchPosts() {
			try {
				this.isPostLoading = true;
				const response = await axios.get(
					"https://jsonplaceholder.typicode.com/posts?_limit=10"
				);
				this.posts = response.data;
			} catch (e) {
				alert("error");
			} finally {
				this.isPostLoading = false;
			}
		},
		
	},
	mounted() {
		this.fetchPosts();
	},
};
</script>

<style scoped>
* {
	padding: 0;
	margin: 0;
	box-sizing: border-box;
}

h2 {
	text-align: center;
}

.app {
	max-width: 780px;
	width: 100%;
	margin: 0 auto;
	text-align: center;
}

.create__btn {
	margin: 12px;
	text-align: right;
	order: 1;
}

@keyframes spin {
	from {
		transform: rotate(0deg);
	}

	to {
		transform: rotate(360deg);
	}
}

.loading:after {
	content: "";
	width: 30px;
	height: 30px;
	top: 0;
	bottom: 0;
	left: 0;
	right: 0;
	margin: auto;
	background: url("@/assets/img/loading_red.png") no-repeat center;
	animation-name: spin;
	animation-duration: 600ms;
	animation-iteration-count: infinite;
	animation-timing-function: linear;
	z-index: 2;
	position: absolute;
}
.app__btns{
	display: flex;
	justify-content: space-between;
}
</style>
