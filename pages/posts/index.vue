<template>
  <v-container>
    <v-row>
      <v-col md="4" v-for="item in posts" :key="item.id">
        <nuxt-link :to="'posts/' + item.id" class="text-decoration-none card-link">
          <v-card class="h-100">
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

<style lang="sass">
.card-link
  display: block
  height: 100%

  .v-card
    height: 100%
</style>
