<template>
  <div class="break">
    <h3 style="color: #030303">打破家庭照顧者五大迷思</h3>
    <p><br></p>
    <p>長久以來，台灣照顧者陷於孝順就是「親力親為」的傳統照顧迷思。高雄市家庭照顧者關懷協會理事長李逸分析，有時是照顧者不放手，總認為「他們照顧沒有我用心」，但時日一久，照顧長輩經常變成一個人的責任。</p>
    <p><br></p>
    <p>但<b>照顧不是一個人的事</b>，照顧者應自我提醒，避免陷入以下5種常見的迷思，並調適自己的心態，千萬不要過度承擔，把自己逼入絕境。</p>
    <p><br></p>
    <div class="breakWhat" v-for='target in break_target' :key='target.TitleIndex'>
      <hr>
      <h3>{{target.TitleIndex}}</h3>
      <hr>
      <b class="icon_size"><i class="fa fa-times" aria-hidden="true"></i>常見的想法：</b>
      <p>{{target.BadThinking}}</p>
      <b class="icon_size orange"><i class="fa fa-circle-o" aria-hidden="true"></i><span>合理的想法：</span></b>
      <p>{{target.GoodThinking}}</p>
      <p><br></p>
    </div>
    <p>資料來源：中華民國家庭照顧者總會</p>
    <p><br></p>
    <p>《聯合報》將於6月25日至28日，連續四天刊出「活躍老化5.0／長照沒有英雄」系列報導，深入探訪照顧者的故事，從他們的故事中，看見家人間分擔照顧責任的難題，並探詢專家建議，試圖為照顧困境找出解方，協助家庭不因長照而崩解，讓長輩安老、家人凝聚。</p>       
  </div>
</template>

<script>
  export default {
    name: 'break',
    data() {
      return {
        break_target: [
          {
            "TitleIndex": "迷思一：照顧就應該要自我犧牲",
            "MainTitle": "照顧就應該要自我犧牲",
            "BadThinking": "我要用生命中的每一分、每一秒來照顧他，直到他痊癒為止，其他的事情都可以放下，等到以後再說。",
            "GoodThinking": "唯有適當地讓自己喘息，才能有更好的照護品質！有足夠休息，才能照顧好患者，因此在條件許可下，可以維持原有的社交活動。" 
          },
          {
            "TitleIndex": "迷思二：100分的照顧才是好的照顧",
            "MainTitle": "100分的照顧才是好的照顧",
            "BadThinking": "只要家人好就好，我沒差；我不該抱怨、生氣，也沒有時間沮喪！",
            "GoodThinking": "唯有我快樂，才會有健康家人。照顧者的情緒會嚴重影響到被照顧者的情緒。" 
          },
          {
            "TitleIndex": "迷思三：只有我最了解他，我來照顧才是最好的",
            "MainTitle": "只有我最了解他，我來照顧才是最好的",
            "BadThinking": "除了我，沒有人可以好好照顧他！我一個人承擔就好！我還撐得下去！",
            "GoodThinking": "照顧者要大方接受協助。支援越多，越能事半功倍。" 
          },
          {
            "TitleIndex": "迷思四：照顧工作是沒有價值的",
            "MainTitle": "照顧工作是沒有價值的",
            "BadThinking": "照顧家人是天經地義的，沒有什麼好鼓勵的。我每天照顧一個家人，對社會沒有貢獻，是一個沒用的人。",
            "GoodThinking": "照顧家人對整個家庭和社會都有重要的意義和貢獻。我做的事情很重要，值得被鼓勵與肯定。" 
          },   
          {
            "TitleIndex": "迷思五：照顧是家裡的事情",
            "MainTitle": "照顧是家裡的事情",
            "BadThinking": "照顧家人已經夠讓人操煩了，我只要盡力就好，不用跟別人說，說也沒有用。",
            "GoodThinking": "我應該多多和有相同或類似經驗的人交流，可以學習到更多的寶貴經驗。" 
          },                                    
        ]
      }
    }
  }
</script>

<style lang="scss" scoped>
h3{
  color: #a84200;
}
hr{
  border-top: 1px solid #b5b5b5;
}
.breakWhat{
  width: 100%;
}
.fa{
  margin-right: 9px;
}
.icon_size{
  font-size: 1.35em;
}
.orange {
  color: #eb6100;
}
</style>