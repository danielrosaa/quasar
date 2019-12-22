<template>
<div>
    <q-btn-group spread>
      <q-btn @click="getPosts" color="primary" label="Load posts" />
      <q-btn @click="clearPosts" color="warning" label="Clear" icon="trash" />
    </q-btn-group>
    <div class="column items-center q-pa-md">
      <h4>Teste de API</h4>
      <div v-if="posts.length === 0">
        <p>No posts</p>
      </div>
      <div v-else v-for="post in posts" :key="post.id" class="text-center">
        <h6>{{post.title}}</h6>
        <p>
          {{post.body}}
        </p>
      </div>
    </div>
</div>
</template>

<script>
export default {
  data () {
    return {
      posts: []
    }
  },
  methods: {
    async getPosts () {
      const { data } = await this.$axios.get('https://jsonplaceholder.typicode.com/posts')
      this.posts = data
    },
    clearPosts () {
      this.posts = []
    }
  }
}
</script>

<style lang="scss">
@for $i from 1 through 6 {
  h#{$i}:not(h1) {
    margin: 0.5em 0;
  }
}
</style>
