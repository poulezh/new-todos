<template>
  <div>
    <h3>List</h3>
    <PostItem 
      v-for="post in posts"
      :post="post"
      :key="post.id"
      @remove="$emit('remove', post)"

      ></PostItem>
  </div>

</template>

<script>
import PostItem from '@/components/PostItem.vue';
export default {
  components: { PostItem },
  props: {
    posts: {
      type: Array,
      required: true
    }
  },

}
</script>

<style scoped>


h3 {
  text-align: center;
}
</style>