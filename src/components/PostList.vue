<template>
  <div v-show="posts.length > 0">
    <h3>List ({{posts.length}})</h3>
    <PostItem 
      v-for="post in posts"
      :post="post"
      :key="post.id"
      @remove="$emit('remove', post)"
      ></PostItem>
  </div>
  <h2 v-show="posts.length === 0">Not Posts</h2>
</template>

<script>
import PostItem from '@/components/PostItem.vue';
export default {
  components: { PostItem },
  props: {
    posts: {
      type: Array,
      required: true
    },

  },


}
</script>

<style scoped>


h3,h2 {
  text-align: center;
}
h2{
  margin-top: 12px;
}
</style>