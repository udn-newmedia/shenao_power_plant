<template>
  <div class="Report_section">
    <Content background-color="#ff">
      <h1>乾淨的煤？<br>拆穿深澳電廠的六大謊言</h1>
      <p><br></p>
      <p>深澳電廠蓋下去，空汙粉塵、一級致癌重金屬飄出來，到底會去哪裡？誰來把關？這座7年後才會蓋好的電廠，現政府早已下台，「剪不了綵的千億工程」環差案悄悄闖關，被猛批還是硬幹，背後到底藏了什麼祕密？</p>
      <p><br></p>
      <p>幾次大跳電，台灣缺電問題浮出水面，反核意識高漲的此刻，措手不及的殺出一座「燃煤電廠」，飽受中火荼毒的台中人痛心疾呼，不要首都也淪陷。全球積極淘汰燃煤電廠，台灣卻要再蓋一座深澳，我們到底賭上什麼風險？</p>
      <p><br></p>
      <Share :href="url"></Share>
    </Content>
    <SectionBg style="background-color: #fff" bg="./static/mobile/pic1.jpg" bgweb="./static/web/pic1.jpg" imgsay="舊深澳電廠於1960年啟用，曾是東南亞發電量最大的電廠，2007年除役。圖中右上方大片平地即是未來深澳電廠預定地。"></SectionBg>
    <Content backgroundColor="#fff">
      <h3>Q1:</h3>
      <h3>環評通過</h3>
      <h3>對環境就沒有影響了嗎？</h3>
      <p><br></p>
      <p>3月14日深夜，環保署副署長詹順貴，在深澳電廠環境影響差異分析（環差）會議8:8的僵局上，以主席的身分投下關鍵支持一票，全案通過環評，讓已除役11年的深澳電廠起死回生，北台灣將在2025年新增一座燃煤電廠。</p>
      <p><br></p>
      <p>當時也在會議中的新北市環保局長劉和然當場憤而離席，引起媒體關注。他擔任過無數場開發案環評審查主席，深知重大爭議案應以「共識決」避免「多數決」，因為被否定掉「少數」並不像一般表決，只代表個人意見，「一票一票，都代表一個專業領域的疑慮跟風險」。</p>
      <p><br></p>
      <p class="extbox"><b>「委員只有十幾個，每個人都來自不同的領域，土木、水土保持、防災、生態、空氣汙染、噪音等等，被否定掉的每個委員背後所代表的、犧牲的都是人民的安全，這些怎麼是可以被多數決抹煞掉的。」</b></p>
      <p><br></p>
      <p>堅決反對的環委、海洋專家鄭明修表示，根據環評法規定，海域監測研究至少需要一至兩年調查，結果深澳的案子，只在去年10月做了一次，「只做一次」。</p>
      <p><br></p>
      <p>環委劉益昌也痛批，台電始終不願意把內容寫清楚，且台電面對環委提出的問題，都只回四字「遵照辦理」，他一直思考，到底該如何面對台電的敷衍，「讓人痛苦」。</p>
      <p><br></p>
      <p>3月14日這場會議，陷入平分僵局就代表開發案還沒準備好，還有許多爭議、風險需要再討論修正，主席有權利不投票、宣布再研議。</p>
      <p><br></p>
      <p>但劉和然在詹順貴走向投票箱時，不斷對他大喊「你可以不投票」，但詹順貴執意走向投票箱，劉和然知道無法挽回，死心離場，離開時見一旁許多大學生、環團都當場哭了出來。</p>
      <p><br></p>
      <p class="extbox"><b>詹順貴在會後受訪表示，「因為我不熟會議規則，而且時間晚了、有環委要趕高鐵。」</b></p>
      <p><br></p>
      <p>東北角地區的居民已自組「反深澳燃煤電廠自救會」，本周赴政院提出訴願。新北市府的律師團也已到位，將依法提出訴願，要求撤銷環評重審，若訴願無效，將持續依循法律途徑提出行政訴訟。</p>
      <p><br></p>
      <ColumnOne img1="./static/mobile/pic2.jpg" imgweb1="./static/web/pic2.jpg" imgsay=""></ColumnOne>
      <p><br></p>
      <ColumnOne img1="./static/mobile/pic3.jpg" imgweb1="./static/web/pic3.jpg" imgsay="深澳灣附近海洋生態豐富，居民嘆未來建造卸煤碼頭，這些珍貴的海底生態將被破壞、永久消失。圖／王銘祥提供"></ColumnOne>
      <p><br></p>
      <h3>Q2:</h3>
      <h3>乾淨的煤？</h3>
      <h3>「我聽了快昏倒」</h3>      
      <p><br></p>
      <p>行政院長賴清德表示，深澳電廠所用的煤是「乾淨的煤」，加上它的設備是<span class="extbtn" @click="showLinkai">「超超臨界」</span>燃煤機組，排放的汙染量跟天然氣發電廠差不多。</p>
      <div v-show="linkaiShow">
        <p><br></p>
        <p class="extbox">指燃煤火力發電機組燃燒技術升級，使燃燒更完全，效率約從38%提高至45%。</p>
      </div>
      <p><br></p>
      <p class="extbox"><b>「差138倍，到底是哪門子的差不多？」長期關注空汙議題的中興大學環工系教授莊秉潔直言，賴清德是被事務官誤導。</b></p>
      <p><br></p>
      <p>台灣目前唯一的「超超臨界」發電機組在林口電廠，相比大潭天然氣發電廠。對眼睛、呼吸道有強烈的刺激作用且恐致急性中毒的二氧化硫，排放量差138倍。造成空汙一大來源的懸浮微粒（PM）也差了48倍。</p>
      <p><br></p>
      <p class="extbox"><b>新北市環保局長劉和然也直呼，「哪有乾淨的煤，我聽了快昏倒！」</b>劉和然表示，賴清德想表達的是「淨煤技術」，但怕民眾聽不懂，就自己說是「乾淨的煤」。</p>
      <p><br></p>
      <p>劉和然進一步說明，淨煤技術其實是一連串環環相扣的技術，通常一個電廠，有3個環節可以讓汙染排放量降低。</p>
      <p><br></p>
      <p>第一個，源頭買好一點的煤，幫助燃燒更完全，但劉和然直言，「台灣沒條件，買什麼煤不是我們決定，有錢人家也不賣給你。」</p>
      <p><br></p>
      <p>第二個，中間燃燒技術升級，讓燃燒更完全，所謂「超超臨界」講的就是這一部分，但效率也只是從以往38%提高至45%。</p>
      <p><br></p>
      <p>第三個，就是過濾。劉和然表示，現今技術，還沒有可以100%過濾致癌汙染物的，不管可以過濾掉多少比例，中山醫學大學公衛系教授廖勇柏曾提醒，層層把關還飄出來的汙染物，因為非常細小，所以不僅可以飄得更遠，汙染範圍更大，對人體攻擊力也是最強的。</p>
      <p><br></p>
      <p class="extbox"><b>劉和然表示，目前台灣要使用的這套日本淨煤技術，廠商在美國蹲點十幾年，至今一套都還賣不出去，就是因為飄出來的重金屬汙染物，是解決不了的問題，達不到美國的標準，林口電廠現就用的就是這一套，「並沒有想像的那麼好」。</b></p>
      <p><br></p>
      <ColumnOne img1="./static/mobile/pic4.jpg" imgweb1="./static/web/pic4.jpg" imgsay="行政院長賴清德（中）3月中視察林口電廠時表示，未來深澳電廠使用的就是與林口電廠相同的超超臨界發電機組與「乾淨的煤」，此說法一出引發爭議。"></ColumnOne>
      <p><br></p>
      <h3>Q3:</h3>
      <h3>深澳的汙染</h3>
      <h3>將使台灣的天空像北京</h3>      
      <p><br></p>
      <p>中興大學環工系教授莊秉潔，以氣象資料模擬空汙煙流，做出汙染範圍圖如下。他發現深澳電廠PM2.5濃度每立方公尺約6.075微克，跟台電報告書中所預估的1.933相差3倍以上。</p>
      <p><br></p>
      <p>天氣風險公司總經理彭啟明，也根據氣流與地形判斷，深澳電廠地勢較低，一旁的峽谷就是基隆河谷，台灣每年約10月開始吹東北風。</p>
      <p><br></p>
      <p>未來汙染物將順著基隆河，從深澳吹入基隆、汐止，進入台北市，每年至少連續半年。而宜蘭縣及桃園市的汙染量，甚至比新北市更高，分別為每立方公尺7.499、6.871微克。</p>
      <p><br></p>
      <p class="extbox"><b>根據莊秉潔的模擬分布圖，深澳電廠的汙染範圍，除了花東地區影響範圍較輕微，其他都會被隨風飄散的汙染物覆蓋，最遠至屏東，影響幾乎遍及全台。</b></p>
      <p><br></p>
      <h3>深澳電廠PM2.5模擬分布圖</h3>
      <ColumnOne img1="./static/mobile/pic5.jpg" imgweb1="./static/web/pic5.jpg" imgsay="註：圖為中興大學環境工程系教授莊秉潔模擬最大日均值<br/>資料來源：中興大學環境工程系教授莊秉潔"></ColumnOne>
      <p><br></p>
      <p>莊秉潔表示，至於夏天吹西南風，對深澳當地環境比較有影響。</p>
      <p><br></p>
      <p class="extbox"><b>但秋天時，台北有熱島效應，尤其秋老虎發威時，協和電廠、林口電廠的汙染全部從高處吹進台北盆地，再被上方的熱空氣像蓋子一樣鎖在盆地裡，未來再加上深澳，會看到台北的空氣品質紅爆紫爆。</b></p>
      <p><br></p>
      <p>莊秉潔說，「我想問一個問題是，目前台北市的空氣品質你是不是滿意，如果你不滿意，你還希望繼續下降嗎？ 」</p>
      <p><br></p>
      <h3>Q4:</h3>
      <h3>燃煤排放致癌重金屬 </h3>
      <h3>台電報告隻字未提</h3>        
      <p><br></p>
      <p>「燃煤發電會排放出鉛、鎘、汞、砷與戴奧辛等，一級致癌重金屬物質。」莊秉潔指著其他學者研究繪製的<a href="http://taiwancancermap.csmu-liawyp.tw/" target="_blank" @click="cancerMap">台灣40年癌症地圖。</a></p>
      <p><br></p>
      <p>他說，在舊深澳電廠運轉期間，深澳及鄰近鄉鎮男性支氣管和肺癌死亡率，明顯高於其他地區。其他男性肺癌死亡率高的地區，如麥寮等西南沿海與宜蘭部分鄉鎮，也多有燃煤電廠分布。</p>
      <p><br></p>
      <p class="extbox"><b>「全台大約5成重金屬排放，來自燃煤電廠。」莊秉潔認為，燃煤電廠排放的重金屬，就是造成男性罹患肺癌的主因。但台電的評估報告，完全沒有提到重金屬排放相關資訊。</b></p>   
    </Content>
  </div>
</template>

<script>
import Utils from 'udn-newmedia-utils'

import ColumnOne from '../base_comp/ColumnOne'
import Content from '../base_comp/Content'
import Cover from '../base_comp/Cover'
import SectionFixedBg from '../base_comp/SectionFixedBg'
import SectionBg from '../base_comp/SectionBg'
import Share from '../base_comp/Share'

export default {
  name: 'Report',
  components: {
    Content,
    Cover,
    ColumnOne,
    SectionBg,
    SectionFixedBg,
    Share
  },
  data() {
    return {
      url: 'https://udn.com/upf/newmedia/2018_data/shenao_power_plant/index.html',
      linkaiShow: false,
    }
  },
  methods: {
    showLinkai () {
      this.linkaiShow === false ? this.linkaiShow = true : this.linkaiShow = false;
      ga("send", {
          "hitType": "event",
          "eventCategory": "spec",
          "eventAction": "click",
          "eventLabel": "[" + Utils.detectPlatform() + "] [" + document.querySelector('title').innerHTML + "] [點擊超超臨界]"
      });      
    },
    cancerMap () {
      ga("send", {
          "hitType": "event",
          "eventCategory": "link",
          "eventAction": "click",
          "eventLabel": "[" + Utils.detectPlatform() + "] [" + document.querySelector('title').innerHTML + "] [點擊台灣40年癌症地圖]"
      });        
    }
  },
  created () {

  },
  mounted () {

  }
}
</script>

<style lang="scss" scoped>
.Report_section{
  position: relative;
  z-index: 5;
  width: 100%;
  background-color: #fff;
  // margin-top: 48px;
  // @media screen and (min-width: 1024px) {
  //   margin-top: 50px;
  // }
}
.extbox{
  padding: 12px;
  background: #eeeeee;
}
.extbtn{
  color: #e13a29;
  text-decoration: underline;
  cursor: pointer;  
}
</style>