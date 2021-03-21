<template>
  <v-container>
    <v-row>
      <v-col sm="12">
        <v-img src="https://placeimg.com/800/400/any/grayscale" />
        <h1>
          {{ post.title }}
        </h1>
        <p>
          {{ post.body }}
        </p>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  async asyncData({$axios, params}) {
    const post = await $axios.$get(
      'https://jsonplaceholder.typicode.com/posts/' + params.id
    )
    return {post}
  },
  data() {
    return {
      post: {}
    }
  }
}
</script>
