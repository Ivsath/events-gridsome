<template>
  <Layout>
    <h1>{{ $page.event.title }}</h1>
  </Layout>
</template>

<page-query>
query($id: ID!) {
  event(id: $id) {
    id
    title
    duration
    price
    date
    image
  }
}
</page-query>

<script>
export default {
  metaInfo() {
    return {
      title: this.$page.event.title,
    }
  },
}
</script>
