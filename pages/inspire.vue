<template>
  <v-row>
    <v-col class="text-center">
      <v-btn color="primary" @click="increment">
        Dashboard {{ count }}
      </v-btn>
      <v-btn color="primary" @click="fetch">
        Fetch
      </v-btn>
      <p v-if="mountains.length">{{ mountains }}</p>
    </v-col>
  </v-row>
</template>

<script>
export default {
  name: 'InspirePage',
  data: () => ({
    count: 0,
    fetchOnServer: false,
    posts: [],
    mountains: [],
  }),
  methods: {
    increment() {
      this.count++
    },
    async fetch() {
      console.log('fetch')
      this.mountains = await fetch(
        'https://api.nuxtjs.dev/mountains'
      ).then(res => res.json())
    }
  },
}
</script>
