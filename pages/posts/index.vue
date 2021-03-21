<template>
  <v-container>
    <v-row>
      <v-col md="4" v-for="item in posts" :key="item.id">
        <nuxt-link :to="'posts/' + item.id" class="text-decoration-none">
          <v-card>
            <v-img src="https://placeimg.com/200/150/any/grayscale" />
            <v-card-title>
              {{ item.title }}
            </v-card-title>
            <v-card-text>
              {{ item.body }}
            </v-card-text>
          </v-card>
        </nuxt-link>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  name: 'posts',
  async asyncData({$axios}) {
    const posts = await $axios.$get(
      'https://jsonplaceholder.typicode.com/posts'
    )
    return {posts}
  },
}
</script>
