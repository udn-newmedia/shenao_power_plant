<template>
  <div class="Report_section">

  </div>
</template>

<script>
export default {
  name: 'Report',
  components: {

  },
  data() {
    return {
      url: 'https://udn.com/upf/newmedia/2018_data/family_caregiver/index.html'
    }
  },
  methods: {
    
  },
  created () {

  },
  mounted () {
    console.log(this.url)
  }
}
</script>

<style lang="scss" scoped>
.Report_section{
  position: relative;
  z-index: 5;
  width: 100%;
  height: 100vh;
  background-color: red;
}
</style>