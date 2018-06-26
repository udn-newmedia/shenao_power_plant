<template>
  <div :id="menuText" class="typingCover">
    <h1 class="typing">{{key}}<span v-show="keyflash" class="flash">❘</span></h1>
    <h1 class="typing">{{key_2}}<span v-show="keyflash_2" class="flash">❘</span></h1>
    <h1 class="typing">{{key_3}}<span v-show="keyflash_3" class="flash">❘</span></h1>
  </div>
</template>

<script>
  import Bus from '../eventBus.js'
  export default {
    name: 'Typing_2',
    props: ['menuText'],
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
        trigger: false,
        typeSpeed: 100,
        typeDelay: 888,
      }
    },
    methods: {
      handle_typeEffect () {
        const words = ['照', '顧', '者', '獨', '白']
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
        const words = ['這', '種', '辛', '酸', '沒', '人', '能', '懂', '.', '.', '.']
        this.keyflash_2 = true
        this.keyInterval = window.setInterval(()=>{
          if(this.keyIndex < words.length){
            this.key_2 = this.key_2.concat(words[this.keyIndex])
            this.keyIndex ++
          } else {
            console.log('clear')
            window.clearInterval(this.keyInterval)
            this.keyIndex = 0
          }
        }, this.typeSpeed)
      },
      handle_scroll () {
        if(window.pageYOffset > this.$el.offsetTop - window.innerHeight/4 && this.trigger === false){
          this.trigger = true
          this.handle_typeEffect()
        }
      },
      handle_Emit: function() {
        const self = this
        Bus.$emit('emitHeadbarTitle', {
          title: self.menuText
        })
      },      
    },
    created () {

    },
    mounted () {
      if(this.menuText !== undefined){
        this.handle_Emit()
      }
      window.addEventListener('scroll', this.handle_scroll)
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
  @media screen and (min-width: 1024px) {
    text-align: left;
  }
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
