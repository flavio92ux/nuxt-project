<template>
  <div>
    <nuxt-link to="/">Voltar</nuxt-link>
    <h1>Comments!</h1>
    <ul>
      <li v-for="comment in comments" :key="comment.id">
        <nuxt-link :to="`${$route.path}/${comment.id}`">{{ comment.name }}</nuxt-link>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      titlePage: 'Comentários',
      descriptionPage: 'Página de comentáriios',
      comments: [],
    }
  },
  head() {
    return {
      title: this.titlePage,
      meta: [
        {
          description: this.descriptionPage,
        }
      ]
    }
  },
  mounted() {
    this.getComments()
  },
  methods: {
    getComments() {
      this.$axios
        .get('comments')
        .then((res) => {
          this.comments = res.data
        })
    }
  },
}
</script>

