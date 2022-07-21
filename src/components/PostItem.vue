<template>
  <div class="post">
    <div>
      <div><strong>Title: </strong> {{ post.title }}</div>
      <div><strong>Desc: </strong> {{ post.body }}</div>
    </div>
    <div>
      <MyButton @click="$emit('remove', post)" class="post__btn">Delete</MyButton>
    </div>

  </div>
</template>

<script>
export default {
    props: {
        post: {
            type: Object,
            required: true
        }
    },
    methods:{

    }
}
</script>

<style scoped>
.post {
  display: flex;
  flex-direction: row;
  align-items: center;
  justify-content: space-between;
  padding: 15px;
  border: 2px solid forestgreen;
  margin: 16px;
  text-align: left;
}
.post div div{
  margin-bottom: 12px;
}
.post__btn{
  background: red;
}
</style>