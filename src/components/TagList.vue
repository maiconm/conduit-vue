<template>
  <div v-if="!tags">
    ⏳ carregando...
  </div>
  <div v-else-if="!tags.length">
    🤷 Não há tags!
  </div>
  <div v-else>
    <a
      v-for="tag in tags"
      :key="tag"
      href="/"
    >
      {{ tag }}
    </a>
  </div>
</template>

<script>
  export default {
    async created() {
      const response = await fetch('https://conduit.productionready.io/api/tags')
      const {tags} = await response.json()
      this.tags = tags.filter(
        tag => tag.replace(/[^a-z0-9]/g, '')
      )
    },
    data() {
      return {
        tags: undefined
      }
    }
  }
</script>

<style scoped>
  a {
    display: inline-block;
    background-color: #818a91;
    color: white;
    padding: .2em .8em;
    white-space: nowrap;
    margin-right: .3em;
    border-radius: 1em;
    font-size: .9em;
  }
</style>
