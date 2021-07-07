<template>

  <TimerComponent />
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import TimerComponent from './components/Timer.vue'
export default {
  components: {TimerComponent },
  setup() {
    return {};
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
