<template>
  <div class="map_container">
    <div id="map" :style="{height: wH + 'px'}"></div>
    <div class="title_box" :style="{height: wH + 'px'}">
      <div class="title_main">
        <h1>台北，下一個北京？</h1>
        <h1>拆穿深澳電廠神話</h1>
        <p>「我其實已經不太記得細節了，只知道很痛。」今年21歲的阿邦（化名）淡淡地說，語氣平靜的像在談論別人的事。第一眼見到阿邦，他笑得燦</p>
        <Share :href="url"></Share>
      </div>
    </div>
    <div class="title_box" :style="{height: wH + 'px'}" ref="showMarker">
      <div class="title_main">
        <p>「我其實已經不太記得細節了，只知道很痛。」今年21歲的阿邦（化名）淡淡地說，語氣平靜的像在談論別人的事。第一眼見到阿邦，他笑得燦</p>
      </div>
      <ul class="marker_info">
        <li><span class="observe_site" :style="{backgroundColor: ObserveColor}"></span>觀測站</li>
        <li><span :style="{backgroundColor: PollutionColor}"></span>汙染原址</li>
      </ul>
    </div>
    <div class="title_box" :style="{height: wH + 'px'}" ref="FlyToShenao">
      <div class="title_main">
        <p>深澳電廠</p>
      </div>
    </div>    
    <div class="title_box" :style="{height: wH + 'px'}" ref="FlyToStation">
      <div class="title_main">
        <p>基隆觀測</p>
      </div>
    </div>   
    <div class="title_box" :style="{height: wH + 'px'}" ref="FlyToStation_2">
      <div class="title_main">
        <p>汐止觀測</p>
      </div>
    </div>  
    <div class="title_box" :style="{height: wH + 'px'}" ref="FlyToStation_3">
      <div class="title_main">
        <p>松山觀測</p>
      </div>
    </div>      
    <div class="title_box" :style="{height: wH + 'px'}" ref="FlyToTaipei">
      <div class="title_main">
        <p>TAIPEI 101</p>
      </div>
    </div>
    <div class="title_box" :style="{height: wH + 'px'}" ref="FlyToBigTaipei">
      <div class="title_main">
        <p>看見雙北</p>
      </div>
    </div>           
  </div>
</template>

<script>
import mapboxgl from 'mapbox-gl';
import _debounce from 'lodash.debounce';
import ColumnOne from '../base_comp/ColumnOne';
import srcRWD from '../mixin/srcRWD.js';
import Share from '../base_comp/Share';
export default {
  name: 'TheMap',
  mixins: [srcRWD],
  components: {
    ColumnOne,
    Share,
  },
  data() {
    return {
      url: 'https://udn.com/upf/newmedia/2018_data/orange-project/',
      wH: window.innerHeight,
      Map: null,
      isFlyed: false,
      ObserveColor: '#09ddf5',
      Observatory: [
        [25.1286484, 121.7563881, '基隆站'],
        [25.0659879, 121.6386743, '汐止站'],
        [25.1797314, 121.6874749, '萬里'],
        [24.9775082, 121.5360221, '新店'],
        [24.984116, 121.4491731, '土城'],   
        [25.0122662, 121.4562882, '板橋'],
        [25.032913, 121.4332029, '新莊'],
        [25.069017, 121.4780249, '菜寮'],
        [25.0766879, 121.3627617, '林口站'],
        [25.1660761, 121.4460768, '淡水'],
        [25.1059048, 121.5125556, '士林'],
        [25.0619756, 121.5235568, '中山'],
        [25.0475499, 121.5085038, '萬華'],
        [25.0205827, 121.5265888, '古亭'],
        [25.0480174, 121.5558915, '松山站'],
        [25.0641802, 121.5108575, '大同'],
        [24.9953096, 121.302173, '桃園']
      ],
      PollutionColor: '#e60012',
      Pollution: [
        [25.127564, 121.816581, '深澳發電廠'],
        [25.119648, 121.298975, '林口發電廠'],
        [24.213376, 120.486809, '台中發電廠'],
        [24.309016, 121.763163, '和平電廠'],
        [23.802677, 120.190312, '麥寮發電廠'],
        [25.157499, 121.739728, '協和發電廠'],
        [22.859005, 120.200540, '興達發電廠'],
        [22.536259, 120.335630, '大林發電廠'],
        [22.552783, 120.354949, '中國鋼鐵'],
        [24.133539, 121.637087, '亞洲水泥花蓮廠'],
        [24.229429, 120.501425, '中龍鋼鐵'],
        [23.798461, 120.217613, '台塑石化麥寮一'],
        [22.784130, 120.558255, '鳳勝實業高樹廠'],
        [24.311874, 121.745778, '合盛礦業'],
        [24.588092, 121.851953, '台泥蘇澳廠'],
        [24.629173, 121.783653, '潤泰水泥冬山廠'],
        [23.801167, 120.212778, '麥寮汽電'],
        [24.552120, 121.755634, '潤泰水泥南澳礦區'],
        [22.755646, 120.584939, '仕和鹽埔碎石廠'],
        [22.702496, 120.321967, '東南水泥'],
        [22.836059, 120.544786, '石裕砂石行'],
        [24.234894, 120.527641, '卜蜂台中廠'],
        [22.705554, 120.333895, '台塑仁武廠'],
        [24.303145, 121.751415, '台泥和平石礦'],
        [24.287306, 120.723726, '正隆后里分公司'],
        [24.593070, 120.810757, '長春石化苗栗廠'],
        [24.3031223,121.7492464, '台泥和平廠'],
        [23.117946,120.326164, '宏遠興業'],
        [22.5597899,120.4030902, '興陽製磚'],
        [24.516755,121.8272893, '幸福水泥東澳廠'],
        [22.829209,120.2957439, '燁聯鋼鐵'],
        [23.7876186,120.1777391, '台塑石化麥寮三'],
        [22.7792274,120.4916407, '尚億開發'],
        [25.032876,121.3012873, '中油桃園煉油廠'],
        [22.6995125,120.3006858, '中油高雄煉油廠'],
        [22.5294178,120.3451698, '中油大林煉油廠'],
        [23.7876516,120.185899, '台塑石化麥寮二'],
        [23.2107435,120.3179803, '台汽共生官田廠'],
        [23.5212379,120.3642116, '台灣化學纖維新港廠'],
        [23.5641466,119.65731, '台電尖山發電廠'],
        [22.4923706,120.4061003, '信昌化工林園廠'],
        [24.3114788,120.7045674, '豐興鋼鐵'],
        [22.4984487,120.4064877, '中油石化事業部'],
        [23.7720346,120.1781789, '台塑麥寮廠'],
        [24.9816027,121.0379832, '永豐餘工業新屋廠'],
        [24.087405, 120.561662, '臺灣化學纖維'],
        [22.724116, 120.341038, '高雄塑酯化工'],
        [24.825204, 121.057734, '遠東化學纖維總廠'],
        [25.029682, 121.051065, '台電大潭發電廠'],
        [24.490921, 120.671016, '台電通霄發電廠'],
        [24.414375, 118.282131, '台電塔山發電廠'],
        [24.009149, 121.636714, '台泥花蓮廠'],
        [22.601919, 120.301034, '台電南部發電廠'],
        [24.609805, 121.826147, '信大水泥南聖湖廠'],
        [22.552496, 120.345587, '台船公司'],
        [23.521701, 120.382457, '南亞塑膠新港廠'],
        [23.090883, 120.274991, '群創光電D廠'],
        [24.124647, 120.582690, '中油台中營'],
        [24.924434, 121.110408, '萬洲化學楊梅一廠'],
        [24.993839, 121.247109, '國瑞汽車中壢廠'],
        [23.727316, 120.588011, '福懋興業'],
        [24.940083, 121.073813, '王佳實業楊梅廠'],
        [24.866218, 121.004677, '三陽新竹廠'],
        [24.206077, 120.619514, '友達光台中廠'],
        [24.386156, 120.753372, '裕隆三義工廠'],
        [23.103121, 120.275968, '群創光電B廠'],
        [22.926563, 120.243667, '奇美公司'],
        [25.060292, 121.109955, '國瑞汽車觀音廠'],
        [23.815450, 120.213213, '台灣化學纖維海豐廠'],
        [23.100867, 120.262047, '群創樹谷分公司'],
        [25.048291, 121.129752, '台光電子材料'],
        [24.430976, 118.342951, '金門酒廠金寧廠'],
        [24.870258, 121.001898, '四維創新材料新竹廠'],
        [24.924467, 121.110394, '萬洲化學楊梅二廠'],        
      ]
    }
  },
  methods: {
    initMap () {
      mapboxgl.accessToken ="pk.eyJ1IjoiYmlsbGZ1bG8iLCJhIjoiY2ppMWZqZDJvMHBhZjNxbGsxN294ZnNtdyJ9.b8mAr_ZiEAPw6hQP6UF9Ng";
      const vm = this;
      this.Map = new mapboxgl.Map({
        container: "map",
        // style: "mapbox://styles/anitpiggy/cji414k0613dk2smzli6oylon",
        style: 'mapbox://styles/billfulo/cjiybqbem3cy62rpm0ylwaox6',
        center: vm.srcRWD([121.161722, 23.618136], [122.541615, 23.511117]),
        zoom: vm.srcRWD(6.5, 7.1),
        interactive: false,
      });       
    },
    goInitail: _debounce(function() {
      const vm = this;
      vm.Map.flyTo({
        center: vm.srcRWD([121.161722, 23.618136], [122.541615, 23.511117]),
        zoom: vm.srcRWD(6.5, 7.1),      
        bearing: 0,
        pitch: 0,                
      })
    }, 1500, {trailing: false, leading: true}),
    goShenao: _debounce(function () {
      const vm = this;
      console.log('深澳電廠')
      $('.observe, .pollution').css({
        'opacity': 0,
        'transition': '0s',
      });
      vm.Map.flyTo({
        center: vm.srcRWD([121.825389, 25.126258], [121.832633, 25.126697]),
        bearing: 0,
        pitch: 0,        
        speed: 1,
        zoom: vm.srcRWD(12.85, 14.5),
      })
      vm.Map.once('moveend', function () {
        console.log('moveend')
        $('.observe, .pollution').css({
          'width': '20px',
          'height': '20px',          
          'transition': 'opacity 666ms',
          'opacity': 1
        });
        $('.station_name').css({
          'opacity': 1
        })        
      })
    }, 1500, {trailing: false, leading: true}),
    goStation: _debounce(function () {
      // 基隆
      const vm = this;
      console.log('基隆站');
      vm.Map.setPaintProperty('keelung_river', 'fill-opacity', 1);
      vm.Map.flyTo({
        center: vm.srcRWD([121.798457, 25.120810], [121.79922, 25.110937]),
        bearing: -106.00,
        pitch: 56.00,
        zoom: vm.srcRWD(12, 13),
        speed: .8,
      })     
    }, 1500, {trailing: false, leading: true}),
    goStation_2: _debounce(function () {
      // 汐止
      const vm = this;
      console.log('汐止站');
      vm.Map.flyTo({
        center: vm.srcRWD([121.589168, 25.046874], [121.63867, 25.065980]),
        bearing: -106.00,
        pitch: 56.00,
        zoom: vm.srcRWD(11.8, 15.04),
        speed: .8,
      })
    }, 2222, {trailing: false, leading: true}), 
    goStation_3: _debounce(function () {
      // 松山
      const vm = this;
      console.log('松山站');
      vm.Map.flyTo({
        center: vm.srcRWD([121.574611, 25.05], [121.558173, 25.051571]),
        bearing: -106.00,
        pitch: 56.00,
        zoom: vm.srcRWD(13.8, 15.92),
        speed: .8,
      })
    }, 2222, {trailing: false, leading: true}),         
    showTaipei: _debounce(function () {
      const vm = this;
      console.log('Taipei101');
      vm.Map.flyTo({
        center: vm.srcRWD([121.564427, 25.033671], [121.5671699, 25.0339031]),
        bearing: 15,
        pitch: 56,
        zoom: vm.srcRWD(15.68, 15.88),
        speed: .8,
      })
    }, 2222, {trailing: false, leading: true}), 
    showBigTaipei: _debounce(function () {
      const vm = this;
      console.log('看見雙北');
      vm.Map.flyTo({
        center: vm.srcRWD([121.604528, 25.000228], [121.684528, 25.062228]),
        bearing: 0,
        pitch: 0,
        zoom: vm.srcRWD(8.5, 10.74),
        speed: .8,
      })
    }, 2222, {trailing: false, leading: true}),          
    addMarker (Lat, Lng, name, color, station) {
      const vm = this;
      const el = document.createElement('div');
      el.className = name;
      if(station === '基隆站' || station === '汐止站' || station === '松山站' || station === '深澳發電廠' || station === '林口站') {
        const text = document.createElement('span');
        text.className = 'station_name';
        text.innerText = station
        el.appendChild(text)
      }
      $('.'+ name).css({
        "height": 10 +'px',
        "width": 10 +'px',
        "border-radius": (name === 'pollution'? 50 : 0) +'%',
        "background-color": color,
        // "border": '1px solid' + color,
        "transition": 'opacity 666ms',
        "opacity": 0,
        "cursor": "pointer",
        "z-index": 3,
      })
      const marker = new mapboxgl.Marker({
        element: el,
      });
      marker.setLngLat([Lng, Lat]);
      marker.addTo(vm.Map);
    },
    addObserve () {
      for(let i = 0; i < this.Observatory.length; i++) {
        this.addMarker(this.Observatory[i][0], this.Observatory[i][1], 'observe', this.ObserveColor, this.Observatory[i][2])
      }
    },    
    addPollution () {
      for(let i = 0; i < this.Pollution.length; i++) {
        this.addMarker(this.Pollution[i][0], this.Pollution[i][1], 'pollution', this.PollutionColor,  this.Pollution[i][2])
      }
    },
    add3Dbuilding () {
      this.Map.addLayer({
          'id': '3d-buildings',
          'source': 'composite',
          'source-layer': 'building',
          'filter': ['==', 'extrude', 'true'],
          'type': 'fill-extrusion',
          'minzoom': 15,
          'paint': {
              'fill-extrusion-color': '#aaa',

              // use an 'interpolate' expression to add a smooth transition effect to the
              // buildings as the user zooms in
              'fill-extrusion-height': [
                  "interpolate", ["linear"], ["zoom"],
                  15, 0,
                  15.05, ["get", "height"]
              ],
              'fill-extrusion-base': [
                  "interpolate", ["linear"], ["zoom"],
                  15, 0,
                  15.05, ["get", "min_height"]
              ],
              'fill-extrusion-opacity': .6
          }
      });      
    },
    handle_scroll () {
      const vm = this
      const curOffset = window.pageYOffset;
      if(this.isFlyed && curOffset < this.$refs.showMarker.offsetTop - this.wH*0.2){
        console.count('goInitail')
        $('.observe, .pollution').css('opacity', 0);
      }
      if(curOffset > this.$refs.showMarker.offsetTop - this.wH*0.2 && curOffset < this.$refs.FlyToShenao.offsetTop - this.wH*0.2) {
        this.isFlyed = true;
        this.goInitail()
        $('.observe, .pollution').css({
          'width': '10px',
          'height': '10px',
          'opacity': 1
        });
        $('.station_name').css({
          'opacity': 0
        })            
        console.log('tick')
      }
      if(curOffset > this.$refs.FlyToShenao.offsetTop - this.wH*0.2 && curOffset < this.$refs.FlyToStation.offsetTop - this.wH*0.2) {
        this.isFlyed = true;
        this.goShenao();            
      }
      if(curOffset > this.$refs.FlyToStation.offsetTop - this.wH*0.2 && curOffset < this.$refs.FlyToStation_2.offsetTop - this.wH*0.2) {
        this.goStation();
        $('.observe, .pollution').css({
          'width': '10px',
          'height': '10px',
          'opacity': 1
        });        
        $('.station_name').css({
          'opacity': 1
        })        
        this.isFlyed = true;
      }
      if(curOffset > this.$refs.FlyToStation_2.offsetTop - this.wH*0.2 && curOffset < this.$refs.FlyToStation_3.offsetTop - this.wH*0.2){
        this.goStation_2();    
        $('.observe, .pollution').css({
          'width': '10px',
          'height': '10px',
          'opacity': 1
        });  
        $('.station_name').css({
          'opacity': 1
        })                 
        this.isFlyed = true;
      }
      if(curOffset > this.$refs.FlyToStation_3.offsetTop - this.wH*0.2 && curOffset < this.$refs.FlyToTaipei.offsetTop - this.wH*0.2){
        this.goStation_3();
        $('.observe, .pollution').css({
          'width': '10px',
          'height': '10px',
          'opacity': 1
        }); 
        $('.station_name').css({
          'opacity': 1
        })               
        this.isFlyed = true;
      }      
      if(curOffset > this.$refs.FlyToTaipei.offsetTop - this.wH*0.2 && curOffset < this.$refs.FlyToBigTaipei.offsetTop - this.wH*0.2) {
        this.showTaipei();
        $('.observe, .pollution').css({
          'width': '10px',
          'height': '10px',
          'opacity': 1
        });       
        $('.station_name').css({
          'opacity': 1
        })         
        this.isFlyed = true;
      }
      if(curOffset > this.$refs.FlyToBigTaipei.offsetTop - this.wH*0.2 && curOffset < this.$refs.FlyToBigTaipei.offsetTop + this.wH) {
        $('.observe, .pollution').css({
          'width': '10px',
          'height': '10px',
          'opacity': 1
        });
        $('.station_name').css({
          'opacity': 1
        })
        this.showBigTaipei();
        this.isFlyed = true;
      }
    },    
  },
  created () {
    console.log(this.wH)
  },
  mounted () {
    const vm = this
    this.$nextTick(()=>{
      this.initMap()
      this.Map.on('load', function (e) {
    // Insert the layer beneath any symbol layer.
        var layers = vm.Map.getStyle().layers;
        vm.add3Dbuilding()
        vm.addObserve()
        vm.addPollution()      
        console.log(layers)
      })
      window.addEventListener('scroll', this.handle_scroll);
      this.handle_scroll();
    })
  }
}
</script>

<style lang="scss">
.map_container{
  display: flex;
  flex-direction: column;
  align-items: flex-end;
  position: relative;
  z-index: 0;
  width: 100%;
}
#map{
  position: fixed;
  top: 0;
  left: 0;
  z-index: -1;
  width: 100%;
}
.title_box{
  position: relative;
  z-index: 0;
  width: 100%;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  background-color: transparent;
  @media screen and (min-width: 1024px) {
    width: 50%;  
  }
}
.title_main{
  width: 100%;
  padding: 0 15px;
  background-clip: content-box;
  background-color: transparent;
  @media screen and (min-width: 1024px) {
    width: 60%;  
  }  
}
.marker_info{
  position: absolute;
  left: -80%;
  bottom: 10vh;
  padding: 5px 15px;
  margin: 0;
  li{
    display: flex;
    align-items: center;
    span{
      display: inline-block;
      margin-right: 10px;
      width: 8px;
      height: 8px;
      border-radius: 50%;
    }
    .observe_site{
      border-radius: 0;
    }
  }
}
.station_name{
  position: absolute;
  top: -25px;
  left: 0;
  width: 25px;
  margin-left: -2.5px;
  white-space: nowrap;
  opacity: 0;
  font-weight: bold;
  font-size: 1.2em;
}
</style>