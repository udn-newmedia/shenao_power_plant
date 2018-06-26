<template>
  <div class="vote">
    <div class='words_section' v-for="(voted, index) in voteData" :key="voted.id">
      <div class="head_section" v-show="showData" :style="{animationDelay: index*66 + 'ms'}">
        <div class="percent"><p>{{Math.round(countTemp[index], -2)}}</p><span class="perIcon">%</span></div>
        <div class="share_words" @click="handle_share(voted.words)">
          <i class="fa fa-share fa-1x" aria-hidden="true" style="display: inline-block;margin-right: 5px;"></i><span>分享</span>
        </div>
      </div>
      <div class="content_section" :style="{backgroundColor: voted.words === checkVote ? '#c0ae9a' : null}">
        <div v-if="!showData" class="choose" @click="handle_vote(index)">{{voteBtn}}</div>
        <p>{{voted.words}}</p>
      </div>
    </div>
    <p><br></p>
    <h3 v-if="showData">感謝你，你已經完成投票！</h3>
  </div>
</template>

<script>
  import axios from 'axios'
  import URLSearchParams from 'url-search-params'
  import _once from 'lodash.once'
  import Utils from 'udn-newmedia-utils'

  export default {
    name: 'Vote',
    data() {
      return {
        voteData: null,
        tempData: null,
        showData: false,
        total: 0,
        countTemp: [0, 0, 0, 0, 0, 0, 0],
        SID: [null, null, null, null, null, null, null],
        voteBtn: '選擇',
        checkVote: ''
      }
    },
    computed: {

    },
    methods: {
      getData () {
        const url = 'https://nmdap.udn.com.tw/caregiver_like/php/vote.php'
        axios.get(url)
          .then((res)=>{
            if(localStorage.getItem('checkVoted') !== null) {
              this.showData = true
              this.checkVote = localStorage.getItem('checkVoted')
              res.data.sort((a, b) => {
                if (a.tick > b.tick) {
                  return -1
                } else if (a.tick < b.tick) {
                  return 1
                } else {
                  return 0
                }
              })
              this.voteData = res.data              
            } else {
              this.voteData = res.data
            }           
          })
          .then((res)=>{
            console.log('data setted')
            window.addEventListener('scroll', this.handle_scroll) 
          })
      },   
      handle_share (word) {
        const newWord = word.replace(/，|、|？|！/gi, '_').slice(0, -1)
        FB.ui({
          method: 'share',
          href: 'https://udn.com/upf/newmedia/2018_data/family_caregiver/index.html',
          hashtag: '#' + newWord
        })
        ga("send", {
            "hitType": "event",
            "eventCategory": "vote",
            "eventAction": "click",
            "eventLabel": "[" + Utils.detectPlatform() + "] [" + document.querySelector('title').innerHTML + "] [" + word + "] [FB分享投票]"
        });      
      },
      handle_vote: _once(function(i) {
        this.handle_click(i);
        this.checkVote = this.voteData[i].words
        ga("send", {
            "hitType": "event",
            "eventCategory": "vote",
            "eventAction": "click",
            "eventLabel": "[" + Utils.detectPlatform() + "] [" + document.querySelector('title').innerHTML + "] [" + this.voteData[i].words + "] [投票]"
        });
        window.localStorage.setItem('checkVoted', this.voteData[i].words);
      }),
      handle_click (i) {
        const url = 'https://nmdap.udn.com.tw/caregiver_like/php/vote.php'
        const params = new URLSearchParams();
        params.append('value', i+1);
        axios.post(url,params)
        .then((res) => {
          res.data.sort((a, b) => {
            if (a.tick > b.tick) {
              return -1
            } else if (a.tick < b.tick) {
              return 1
            } else {
              return 0
            }
          })
          return res.data
        })
        .then((res)=>{
          this.voteData = res
          this.$forceUpdate()
        })
        .then((res)=>{
          this.$nextTick(()=>{
            this.showData = true
            for(let i = 0; i < 7; i++) {
              this.countPercent(i)
            } 
          })             
        })        
        .catch((err) => {
          console.log(err)
        })
      },
      countPercent (index) {
        let tempNum = 0;
        for (let i = 0; i < 7; i++) {
          tempNum += this.voteData[i].tick
        }         
        this.SID[index] = setInterval(() => {
          const maxCount = Math.floor(this.voteData[index].tick / tempNum * 100)
          if(this.countTemp[index] < maxCount){
            this.countTemp[index] += maxCount / 20
            this.$forceUpdate()
          } else {
            const vm = this
            clearInterval(vm.SID[index])
          }
        }, 88)
      },
      handle_scroll () {
        let currentH = window.pageYOffset;
        if (currentH > this.$el.offsetTop - window.innerHeight * 0.33) {
          this.handle_countPercent()
          window.removeEventListener('scroll', this.handle_scroll)
        }
      },
      handle_countPercent: _once(function(){
        if(this.showData === true) {
          for(let i = 0; i < this.voteData.length; i++) {
            this.countPercent(i)
          }
        }
      })
    },
    created () {
      console.log('created')
      this.getData()
    },
    beforeMount () {

    },
    mounted () {
      
    }, 
    updated () {
      console.log('updated')
    }
  }
</script>

<style lang="scss" scoped>
.vote{
  position: relative;
  width: 100%;
  display: flex;
  flex-direction: column;
}
.words_section{
  width: 100%;
  display: flex;
  flex-direction: column;
  margin-bottom: 15px;
  transition: order 1111ms ease-in-out;
}
.head_section{
  height: 50px;
  color: #ec6941;
  display: flex;
  align-items: flex-end;
  margin-bottom: 10px;
  animation: fadeIn 666ms ease-out both;
}
.percent{
  display: flex;
  align-items: flex-end;
  font-size: 60px;
  p{
    line-height: .8 !important;
    font-size: inherit !important;
    margin: 0;
  }
}
.perIcon{
  display: block;
  font-size: 50%;
  color: inherit;
  margin-right: 20px;
  line-height: 1;
}
.share_words{
  display: inline-flex;
  height: 30px;
  width: 180px;
  justify-content: center;
  align-items: center;
  border: 1px solid #ec6941;
  border-radius: 18px;
  cursor: pointer;
}
.content_section{
  display: flex;
  align-items: center;
  background-color: #eee6d9;
  padding: 15px;
  p{
    margin: 0;
    padding: 0;
    @media screen and (min-width: 1024px) {
      padding: 0;
    }
  }
}
.choose{
  flex-shrink: 0;
  width: 5em;
  height: 3em;
  display: flex;
  align-items: center;
  justify-content: center;
  background-color: #a6937c;
  border-radius: 10px;
  color: #fff;
  margin-right: 12px;
  @media screen and (min-width: 1024px) {
    margin-right: 20px;
  }
  cursor: pointer;
}
@keyframes fadeIn {
  from {
    opacity: 0;
  }

  to {
    opacity: 1;
  }
}
</style>
