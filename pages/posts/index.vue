<template>
  <div class="posts-page">
    <PostList :posts="loadedPosts" />
  </div>
</template>

<script>
import PostList from "~/components/posts/PostList";

export default {
  components: {
    PostList
  },
  asyncData(context) {
    return new Promise((resolve, reject) => {
      setTimeout(() => {
        resolve({
          loadedPosts: [
            {
              id: "1",
              title: "First Post",
              previewText: "Some amazing content",
              thumbnail:
                "https://images.unsplash.com/photo-1461749280684-dccba630e2f6?ixid=MnwxMjA3fDB8MHxzZWFyY2h8MXx8Y29kaW5nfGVufDB8fDB8fA%3D%3D&ixlib=rb-1.2.1&w=1000&q=80"
            },
            {
              id: "2",
              title: "Second Post",
              previewText: "Some amazing content",
              thumbnail:
                "https://images.unsplash.com/photo-1461749280684-dccba630e2f6?ixid=MnwxMjA3fDB8MHxzZWFyY2h8MXx8Y29kaW5nfGVufDB8fDB8fA%3D%3D&ixlib=rb-1.2.1&w=1000&q=80"
            }
          ]
        });
      }, 1000);
    }).then(data => {
      return data;
    });
  },
  created() {
    this.$store.dispatch('setPosts', this.loadedPosts)
  }
};
</script>

<style scoped>
.posts-page {
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>
