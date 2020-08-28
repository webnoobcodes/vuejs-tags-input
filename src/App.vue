<template>
  <div id="app">
    <TagsInput />
  </div>
</template>

<script>
import TagsInput from './components/TagsInput'

export default {
  name: 'App',
  components: {
    TagsInput
  },
}
</script>

<style lang="scss">
* {
    box-sizing: border-box;
  }

  body {
    margin: 0;
    padding: 0;
    font-size: 1rem;
    font-family: Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
  }

  #app {
    display: flex;
    justify-content: center;
    align-items: center;
    flex-direction: column;
    width: 100%;
    min-height: 100vh;
    padding: 16px;
    background: url('./assets/app_bg.jpg') center center;
    background-size: cover;
  }
</style>
