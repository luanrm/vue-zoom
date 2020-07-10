<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <Meeting/>
  </div>
</template>

<script>
import Meeting from './components/Meeting.vue'

export default {
  name: 'App',
  components: {
    Meeting
  }
}
</script>

