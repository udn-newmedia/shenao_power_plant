<template>
  <div class="careProfile">
    <slot></slot>
    <p><br></p>
  </div>
</template>

<script>
  export default {
    
  }
</script>

<style lang="scss" scoped>
.careProfile{
  background-color: #dcdcdc;
  padding: 15px 15px;
  @media screen and (min-width: 1024px) {
    padding:  10% 12.5%;
  }
}
hr{
  height: 1px;
  background-color: #b5b5b5;
  border-top: solid 1px #b5b5b5;
}
</style>
