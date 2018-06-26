<template>
    <div :id="menuText" class="cover" :style="{backgroundImage: 'url(' + bgRWD() + ')'}" :class="{top: top, bottom: bottom, aligncenter: aligncenter}">
        <div id="title-contain">
            <h1 :style="{color: fontColor}">{{title}}</h1>
            <div id="sub-title" :style="{color: fontColor}">{{subtitle}}</div>
        </div>
        <slot class="slotContainer"></slot>
        <Arrow v-if="useArrow" :color='arrowColor' :hint='hint' :hintColor='hintColor'/>
    </div>
</template>

<script>

import Arrow from './Arrow.vue'
import Bus from '../eventBus.js'

export default {
    name: 'Cover',
    props: ['title', 'subtitle', 'bg', 'bgweb', "position", "arrowColor", "hint", "hintColor", 'useArrow', 'menuText', 'fontColor'],
    data: function(){
        return{
            aligncenter: false,
            top: false,
            bottom: false,
        }
    },
    created: function(){
        window.addEventListener('resize', () => {
            this.$forceUpdate()
        })
        if(this.position == 'top'){
            this.top = true
        }
        if(this.position == 'bottom'){
            this.bottom = true
        }
        if(this.position == 'middle'){
            this.aligncenter = true
        }
    },
    mounted () {
      this.handle_Emit()
    },
    methods: {
        bgRWD: function(){
            if(window.innerWidth <= 768){
                if(window.matchMedia("(orientation: landscape)").matches){
                    return this.bgweb
                }
                else{
                    return this.bg
                }
            }
            else{
                return this.bgweb
            }
        },
        handle_Emit: function() {
          const self = this
          Bus.$emit('emitHeadbarTitle', {
            title: self.menuText
          })
        },
    },
    components: {Arrow}
}
</script>

<style lang="scss" scoped>
    #title-contain{
        width: 100%;
        padding: 20px;
        color: #fff;
    }
    .cover{
      position: relative;
      height: 100%;
      background-position: center center;
      background-repeat: no-repeat;
      background-size: cover;
      overflow: hidden;
      display: flex;
      flex-direction: column;
      justify-content: center;
      align-items: center;
      padding: 12% 8%;
    }
    .cover.top{
        justify-content: flex-start;
    }
    .cover.bottom{
        justify-content: flex-end;
    }
    .aligncenter{
        align-items: center;
    }
    .slotContainer{
      position: absolute;
      top: 0;
      left: 0;
      right: 0;
      bottom: 0;
    }
    h1{
        font-size: 55px;
        font-weight: bold;
        letter-spacing: -1px;
        color: #fff;
        line-height: 1.1;
        // text-shadow: 0 0px 18px rgba(48,48,48,1);
        // text-shadow: 4px 4px 10px rgba(0,0,0,.6);
        margin: 0;
    }
    #sub-title{
        font-size: 55px;
        // text-shadow: 4px 4px 10px rgba(0,0,0,.6);
        // text-shadow: 0 0px 9px rgba(48,48,48,1);
        color: #fff;
    }
    @media screen and (max-width: 767px) {
        h1{
            font-size: 40px;
        }
        #sub-title{
            font-size: 25px;
        }
        .cover{
            padding: 30% 0;
        }
    }

    @media screen and (min-width: 768px) and (max-width: 1024px) {
        h1{
            font-size: 45px;
        }
        #sub-title{
            font-size: 30px;
        }
        .cover{
            padding: 30% 0;
        }
        #title-contain{
            padding: 0 100px;
        }
    }

</style>
