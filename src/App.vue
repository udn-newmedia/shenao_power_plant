<template>
  <div id="app">
    <TheMap></TheMap>
    <Report></Report>
  </div>
</template>

<script>
import Report from '@/components/Report.vue';
import TheMap from '@/components/TheMap.vue';

export default {
  name: 'App',
  components: {
    Report,
    TheMap
  }
}
</script>

<style>
#app {
  position: relative;
  font-size: 16px;
  line-height: 1.5;
  font-family: Arial, Microsoft JhengHei, "微軟正黑體", sans-serif;
  word-wrap: break-word;
  text-align: justify;
  height: 100vh;
}
</style>
