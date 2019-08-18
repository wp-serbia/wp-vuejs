<template>
  <footer>
    &copy; 2019 <a href="https://www.joomlaserbia.info">Joomla Serbia</a>.
  </footer>
</template>

<script>
  export default {
    name: 'Foot'
  }
</script>

<style scoped lang="scss">
  footer {
    text-align: center;
    padding: 1rem;
    background: $gray--light;
  }

  a {
    font-weight: bold;
  }
</style>
