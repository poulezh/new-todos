<template>
	<div class="app">
		<PostForm @create="createPost"></PostForm>
		<PostList 
			:posts="posts"
			@remove="removePost"
		></PostList>
	</div>
</template>

<script>
import { remove } from '@vue/shared';
import PostForm from "./components/PostForm.vue";
import PostList from "./components/PostList.vue";
export default {
	components: {
    PostForm,
    PostList
},
	data() {
		return {
			posts: [
				{ id: 1, title: 'Title1', body: 'desc1' },
				{ id: 2, title: 'Title2', body: 'desc2' },
			],
		};
	},
	methods: {
		createPost(post){
			this.posts.push(post)
		},
		removePost(post){
			this.posts = this.posts.filter(p => p.id !== post.id)
		}
	},
};
</script>

<style scoped>
* {
	padding: 0;
	margin: 0;
	box-sizing: border-box;
}

.app {
	max-width: 780px;
	width: 100%;
	margin: 0 auto;
}

</style>