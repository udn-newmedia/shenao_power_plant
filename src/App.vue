<template>
  <div id="app">
    <Indicator color="#000"></Indicator>
    <HeadBar MenuSlideFrom='right' background-color="transparent" noMenu="true"></HeadBar>
    <div class="ShenaoVideo">
      <video :src="srcRWD(Mvideo, Pvideo)" :poster="srcRWD(Mposter, Pposter)" playsinline muted controls autoplay width="1980" height="1080" ref="Pvideo"></video>
    </div>
    <Report></Report>
    <SectionFixedBg bg="./static/mobile/pic6.jpg" bgweb="./static/web/pic6.jpg"></SectionFixedBg>
    <div class="addScroll"></div>
    <SectionFixedBg bg="./static/mobile/pic7.jpg" bgweb="./static/web/pic7.jpg"></SectionFixedBg>
    <Content backgroundColor="#fff" class="contentLayer">
      <p>「我最大的擔憂就是空氣汙染。」劉和然說，新北市政府沒有反對蓋發電廠，但不該將燃煤發電作為選項。</p>
      <p><br></p>
      <p>新北市去年全市PM2.5年平均值為17.1微克，接近環保署空氣品質標準15微克，「我們努力了5、6年，PM2.5好不容易降下來，現在又要蓋一座深澳電廠，新北市的空品要達標更是遙遙無期。」</p>
      <p><br></p>
      <p class='extbox'><b>日前台北市長柯文哲面對議員質詢，支不支持深澳電廠擴建計畫，他不願正面回應，僅表示，「確定的一件事是，只要興建電廠，過去3年台北市在減少PM2.5的努力，就前功盡棄。」</b></p>
      <p><br></p>
      <ColumnOne img1='./static/mobile/pic8.jpg' imgweb1='./static/web/pic8.jpg'
                 imgsay="若未來北台灣再增加一座深澳燃煤電廠，北部的天空和環境生態恐怕要跟著淪陷。"></ColumnOne>      
      <p><br></p>
      <h3>Q5:</h3>
      <h3>為什麼世界各國</h3>
      <h3>都不再興建燃煤電廠？</h3>  
      <p><br></p>
      <p>法國總統馬克宏（Emmanuel Macron）在世界經濟論壇（World Economic Forum）上矢言，將在2021年關閉所有燃煤火力發電廠。英國目前還剩下的8座，其中1座今年將停產，其他將在2025年之前全數關閉。</p>
      <p><br></p>
      <p class="extbox"><b>就連中國，也在嘗盡空汙的苦果後，去年宣布取消150多座正在興建中的燃煤發電廠。</b></p>
      <p><br></p>
      <p>環團綠色和平減煤專案主任蔡佩芸說明，減煤是國際共識，巴黎協議2050年前淘汰所有燃煤電廠。加上全球人民的空汙意識漸強，燃煤帶來大量的硫氧化物、重金屬、PM2.5，各國政府正積極管制。</p>
      <p><br></p>
      <p>除了汙染，成本也是各國重要考量，綠色和平追蹤全球燃煤發電跟再生能源發展的趨勢，發現2016至2017年間，燃煤場新建量少了一半，再生能源的成本則不斷下降。</p>
      <p><br></p>
      <p>中興大學環工系教授莊秉潔證實，根據台電去年度的發電成本報告，發現台灣燃煤電廠前年發一度電1.1元，去年漲到1.35元。台大風險中心試算，深澳電廠投資費用更高，一度發電成本更將達1.8元。</p>
      <p><br></p>
      <p class="extbox"><b>莊秉潔建議，深澳電廠若非建不可，若不能改用再生能源，至少也要改用天然氣。</b></p>
      <p><br></p>
      <p>外界擔憂天然氣成本過高，但莊秉潔實際試算，深澳電廠目前一度電成本是1.8元，跟2.1元的天然氣僅差一成，民眾與其砸大錢買空氣清淨機，不如從源頭就控制汙染。</p>
      <p><br></p>
      <p>台電日前回應，沒有地方蓋天然氣儲存槽，牽管線也困難度高。莊秉潔則表示，儲存槽可設在海外，英國早在12年前就成功牽設超過100公尺深、長達1200公里的海管，深澳若要作，無論深度或長度，難度都遠小於當時的工程，台灣現在許多重大工程都由外國企業承攬，技術不是問題。</p>
      <p><br></p>
      <p>海洋專家中研院研究員陳昭倫對此作法也認同，他表示，布海管只是短時間的生態干擾，只要持續監測、把關施工，海洋生態都會回到穩定的狀態。</p>
      <p><br></p>
      <p>深澳電廠執意興建，但新北市目前態度堅決，將不會同意核發生煤許可。</p>
      <p><br></p>
      <p class="extbox"><b>新北市環保局長劉和然向中央喊話，堅持要蓋，屆時無煤可燒，只能像核四一樣封存，1000億付諸流水，都是人民納稅錢。</b></p>    
      <p><br></p>
      <ColumnOne img1="./static/mobile/pic9.jpg" imgweb1="./static/web/pic9.jpg" imgsay="撤回深澳電廠連署已破9萬人，民眾以實際行動捍衛呼吸權。你呢？你支持再蓋一座深澳電廠嗎？"></ColumnOne>
      <p><br></p>
      <h3>Q6:</h3>
      <h3>連蓋菜市場都要開100場協調會</h3>
      <h3>深澳電廠，到底急什麼？</h3>  
      <p><br></p>
      <p>台北最大傳統市場「環南市場」，光是改建就討論了18年、開了100場以上的協調會。但影響範圍更深更廣的深澳電廠，卻一夕之間就闖關成功，不少民眾質疑，到底在急什麼？</p>
      <p><br></p>
      <p>不少商界人士私下透露，民進黨是這麼會選舉的政黨，怎麼會不知道深澳電廠是會引發民眾反彈的「失分題」，至於什麼原因，會讓執政黨不惜犧牲民調與選票，「想也知道，電廠背後利益，早就都分配好了。」</p>
      <p><br></p>
      <p>天氣風險公司總經理彭啟明表示，電廠要蓋沒有不行，但還是要有完整、開放的資料，好好來說服民眾，透明公開的，接受來自民間的挑戰跟檢驗。</p>
      <p><br></p>
      <p class="extbox"><b>「不然老實說，就連我是半個局內人、有在參與討論的專業人士，都覺得資料非常零散，這絕對不是一個民主政府處理事情應有的態度。」</b></p>
      <p><br></p>
      <p>深澳電廠3月環評闖關成功時，環保團體綠色和平民調，高達84.2%北北基地區民眾，不知道政府正在規劃興建深澳燃煤電廠。進一步詢問，75.1%民眾反對興建，連署撤回「深澳電廠更新擴建計畫」人數已破9萬人。</p>
      <p><br></p>
      <p class="extbox"><b>「停水、停電，好歹都會在門口貼一張通知單，為什麼住家附近蓋一座這麼大的電廠，居民卻連知的權利都沒有？」深澳居民、台大歷史系副教授衣若蘭表示。</b></p>
      <p><br></p>
      <p>台電除了前年在深澳三里一漁會舉行座談會，沒再向當地居民公開說過電廠規畫。瑞芳文史工作者林文清說，瑞芳區公所曾邀請台電辦座談會，台電回覆是「謝謝指教」，再無下文。</p>
      <p><br></p>
      <p>深澳漁民吳智欽說，要支持可以，但應該跟居民說明。居民黃嚴德也氣憤地說，電廠把環境都破壞，「老伙仔都是肺癌走的，哪有什麼乾淨的煤、什麼里民都支持，黑白講！」</p>
      <p><br></p>
      <p>雖然民進黨政府勾勒深澳電廠如何的美好，然而，事實是，一旦深澳電廠啟用，至少台北市、新北市、桃園市、基隆市及宜縣共950萬、全體台灣4成的人口，將住在大氣汙染的蒼穹之下，北台灣的天空將經常是霧朦朦的、汙濁的。</p>
      <p><br></p>
      <p>你／妳，支持政府興建深澳電廠嗎？</p>
      <p><br></p>
      <p><br></p>
      <p>針對此篇報導，台電做出回應，附上<a href="http://www.taipower.com.tw/tc/news_info.aspx?id=1647&chk=613b9f35-5602-49fd-b2ab-5ca058db44f8&mid=17" target="_black">全文連結</a>。</p>
      <p><br></p>
      <Share :href="url"></Share>
      <Logo></Logo>
      <p><br></p>
      <Editor>
        <div>製作：連珮宇、蔡佩蓉</div>
        <div>採訪團隊：蔡惠萍、連珮宇、蔡佩蓉</div>
        <div>視覺設計：許瑋琳</div>
        <div>網頁製作：廖克樸</div>
        <div>圖：報系資料照</div>
        <div>監製：林新輝、潘如瑩、董谷音、蔡幸怡</div>
        <div>2018.07.17</div>
      </Editor>
      <p><br></p>
      <Question href='https://www.surveycake.com/s/KpQKN' text='填寫閱讀體驗問卷'></Question>
      <p><br></p>
      <Relate
        title="延伸閱讀" color="#363434"
        href1="https://udn.com/news/story/7314/3242458" img1="./static/relate/s1.jpg" text1="反深澳自救會 對政院提訴願"
        href2="https://udn.com/news/story/11981/3074149" img2="./static/relate/s2.jpg" text2="煤電廠回來 深澳潛水天堂將消失？"
        href3="https://udn.com/news/story/11898/3032659" img3="./static/relate/s3.jpg" text3="非核家園神主牌 用全民健康陪葬？"
        href4="https://udn.com/news/story/11981/3089107" img4="./static/relate/s4.jpg" text4="深澳案 李應元：保育區沒說不能開發"
      ></Relate>
      <p><br></p>
      <FbComment :href="url"></FbComment>      
    </Content>
  </div>
</template>

<script>
import Indicator from '@/base_comp/Indicator';
import HeadBar from '@/base_comp/HeadBar';
import Report from '@/components/Report.vue';

import Content from '@/base_comp/Content'
import ColumnOne from '@/base_comp/ColumnOne'
import ColumnTwo from '@/base_comp/ColumnTwo'
import Editor from '@/base_comp/Editor'
import FbComment from '@/base_comp/FBComment'
import Logo from '@/base_comp/Logo'
import Question from '@/base_comp/Question'
import Relate from '@/base_comp/Relate'
import SectionFixedBg from '@/base_comp/SectionFixedBg'
import SectionBg from '@/base_comp/SectionBg'
import Share from '@/base_comp/Share'

import srcRWD from '@/mixin/srcRWD.js'

import Pvideo from '@/assets/Pvideo.mp4'
import Mvideo from '@/assets/Mvideo.mp4'
import Pposter from '@/assets/Pposter.jpg'
import Mposter from '@/assets/poster.jpg'
export default {
  name: 'App',
  mixins: [srcRWD],
  components: {
    ColumnOne,
    ColumnTwo,
    Content,
    Editor,
    FbComment,
    Logo,
    HeadBar,
    Indicator,
    Question,
    Report,
    Relate,
    SectionFixedBg,
    SectionBg,
    Share
  },
  data() {
    return {
      url: 'https://udn.com/upf/newmedia/2018_data/shenao_power_plant/index.html',
      Pvideo: Pvideo,
      Mvideo: Mvideo,
      Pposter:Pposter,
      Mposter:Mposter       
    }
  },
}
</script>

<style lang="scss">
#app {
  position: relative;
  font-size: 16px;
  line-height: 1.5;
  font-family: Arial, Microsoft JhengHei, "微軟正黑體", sans-serif;
  word-wrap: break-word;
  text-align: justify;
  height: 100vh;
}
.contentLayer{
  position: relative;
  z-index: 5;
  width: 100%;
}
.addScroll{
  position: relative;
  height: 50vh;
}
.extbox{
  padding: 12px;
  background: #eeeeee;
}
.ShenaoVideo{
  position: relative;
  z-index: 50;
  width: 100%;
  video{
    width: 100%;
    height: auto;
  }
}
</style>
