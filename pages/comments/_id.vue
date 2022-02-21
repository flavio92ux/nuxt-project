<template>
  <div>
    <h1>{{ comment.name }}</h1>
    <br>
    <p>{{ comment.id }}</p>
    <a :href="`mailto:${comment.email}`">{{ comment.email }}</a>
  </div>
</template>

<script>
export default {
  data() {
    return {
      comment: {}
    }
  },
  mounted() {
    this.getComment()
  },
  methods: {
    getComment() {
      this.$axios
        .get(`comments/${this.$route.params.id}`)
        .then((res) => {
          this.comment = res.data
        })
    }
  }
}
</script>
