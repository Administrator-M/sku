<template>
  <div id="app">
    <!-- <img src="./assets/logo.png">
    <div>
      <el-button @click="startHacking">Start</el-button>
    </div> -->
    <hello />
  </div>
</template>

<script>
import hello from './components/hello.vue';
export default {
  components: {
    hello
  },
  methods: {
    startHacking () {
      this.$notify({
        title: 'It works!',
        type: 'success',
        message: 'We\'ve laid the ground work for you. It\'s time for you to build something epic!',
        duration: 5000
      })
    }
  }
}
</script>

<style>
*{
  margin: 0;
  padding: 0;
}
#app {
  /* font-family: Helvetica, sans-serif; */
}
</style>
