<template>
  <form @submit.prevent>
    <h4>Create post</h4>
    <MyInput v-model="post.title" placeholder="title"></MyInput>
    <MyInput v-model="post.body" class="input" placeholder="desc"></MyInput>
    <MyButton @click="createPost" class="form__btn">Create</MyButton>
  </form>
</template>

<script>

export default {
    data() {
        return {
            post: {
                title: "",
                body: ""
            }
        };
    },
    methods: {
        createPost() {
            this.post.id = Date.now();
            this.$emit("create", this.post);
            this.post = {
                title: "",
                body: ""
            };
        },
    },
}
</script>

<style scoped>
form {
  display: flex;
  flex-direction: column;
  gap: 8px;
  border-bottom: 2px solid forestgreen;
}

form h4 {
  text-align: center;
}

.form__btn{
  margin: 16px;
  background: forestgreen;
  
}
</style>