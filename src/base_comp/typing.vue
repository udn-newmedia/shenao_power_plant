<template>
  <div class="typingCover">
    <h1 class="typing">{{key}}<span v-show="keyflash" class="flash">❘</span></h1>
    <h1 class="typing">{{key_2}}<span v-show="keyflash_2" class="flash">❘</span></h1>
    <h1 class="typing">{{key_3}}<span v-show="keyflash_3" class="flash">❘</span></h1>
  </div>
</template>

<script>
  export default {
    name: 'Typing',
    data () {
      return {
        key: '',
        key_2: '',
        key_3: '',
        keyflash: true,
        keyflash_2: false,
        keyflash_3: false,
        keyInterval: null,
        keyIndex: 0,
        typeSpeed: 100,
        typeDelay: 888,
      }
    },
    methods: {
      handle_typeEffect (target) {
        const words = ['你', '為', '什', '麼', '要', '把', '媽', '媽', '送', '進', '安', '養', '中', '心', '？']
        this.keyInterval = window.setInterval(()=>{
          if(this.keyIndex < words.length){
            this.key = this.key.concat(words[this.keyIndex]);
            this.keyIndex ++
          }
          else {
            window.clearInterval(this.keyInterval)
            this.keyIndex = 0
            setTimeout(()=>{
              this.keyflash = false
              this.handle_typeEffect_2()
            }, this.typeDelay)
          }
        }, this.typeSpeed)
      },
      handle_typeEffect_2 () {
        const vm = this;
        const words = ['為', '什', '麼', '不', '幫', '你', '爸', '請', '個', '外', '勞', '？']
        this.keyflash_2 = true
        this.keyInterval = window.setInterval(()=>{
          if(this.keyIndex < words.length){
            this.key_2 = this.key_2.concat(words[this.keyIndex])
            this.keyIndex ++
          } else {
            window.clearInterval(this.keyInterval)
            this.keyIndex = 0
            setTimeout(()=>{
              // this.keyflash_2 = false
              // this.handle_typeEffect_3()
              if(window.pageYOffset <= this.$el.clientHeight - window.innerHeight/3){
                $('html, body').animate({
                  scrollTop: vm.$el.clientHeight + 'px'
                }, 1000)
              }              
            }, this.typeDelay)
          }
        }, this.typeSpeed)
      },
      // handle_typeEffect_3 () {
      //   const words = []
      //   this.keyflash_3 = true
      //   this.keyInterval = window.setInterval(()=>{
      //     if(this.keyIndex < words.length){
      //       this.key_3 = this.key_3.concat(words[this.keyIndex])
      //       this.keyIndex ++
      //     } else {
      //       window.clearInterval(this.keyInterval)
      //       setTimeout(()=>{
      //         if(window.pageYOffset <= this.$el.clientHeight - window.innerHeight/3){
      //           $('html, body').animate({
      //             scrollTop: window.innerHeight+'px'
      //           }, 1000)
      //         }
      //       }, this.typeDelay)
      //     }
      //   }, this.typeSpeed)
      // }
    },
    created () {

    },
    mounted () {
      this.handle_typeEffect()
    }
  }
</script>

<style lang="scss" scoped>
.typingCover{
  position: relative;
  z-index: 5;
  width: 100%;
  height: 100vh;
  padding: 80px 25px 50px 25px;
  background-color: #7e6b5a;
  color: #ffffff;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: flex-start;
  @media screen and (min-width: 1024px) {
    align-items: center;
  }
}
.typing{
  display: inline;
  line-height: 1.5;
}
.flash{
  font-size: inherit;
  animation: flashType 666ms ease-in-out infinite alternate both;
}
@keyframes flashType {
  from{
    opacity: 0;
  }
  to{
    opacity: 1;
  }
}
</style>
