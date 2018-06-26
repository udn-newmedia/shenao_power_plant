<template>
  <div class="talkSection">
    <div class="talkBox" v-for="word in talk" :key="word">
      <p>{{word}}</p>
    </div> 
  </div>
</template>

<script>
  export default {
    name: 'TalkSection',
    components:{

    },
    data() {
      return {
        talk: [
          '你可以多出去走走透透氣，安排自己的生活，不要因為照顧過度犧牲自己。',
          '有任何需要我們幫忙的地方請儘管提出來，照顧的問題不是你一個人的事情。',
          '照顧是大家共同的責任，不要把所有責任都攬在自己身上。',
          '照顧是難事，盡力就好，不要苛責自己。',
          '自己的身體也要顧，我們愛你，希望你健康。',
          '不要因為放心不下病人而不出門，休息充電後，也可以提升照顧效能。',
          '謝謝你照顧生病的家人，你要肯定自己，你好棒！',
          '照顧是一條漫長的路，可以多了解、多使用長照資源，讓這條路走得更輕鬆。'
        ]
      }
    },
  }
</script>

<style lang="scss" scoped>
.talkSection{
  width: 100%;
  display: flex;
  flex-wrap: wrap;
  align-items: center;
  justify-content: center;
}
.talkBox{
  position: relative;
  width: 100%;
  padding: 12px 25px;
  border-radius: 22.5px;
  display: flex;
  align-items: center;
  color: #030303;
  background-color: #eee6d9;
  margin-bottom: 15px;
  p{
    margin: 0;
  }
}
</style>
