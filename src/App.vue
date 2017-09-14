<template>
	<div id="app">
		<Indicator color="#000000" />
		<HeadBar />
		<Cover title="貧窮世襲<br />被遺忘的孩子" title-bottom="65" title-left="40" title-width="270" title-height="95"/>
		<div class="blank"></div>
		<Content-Text>
			<p>從車站到學校，沿途都是荒煙蔓草，雜草比人高，幾乎把車道掩埋。在這裡，有個小女孩住在貨櫃屋裡。</p>
			<p><br/></p>
			<p>她剛學會走路時，就跟著爸爸從花蓮流浪到台中、彰化、雲林，最後在西螺大橋下遊蕩，沒有居所。</p>
			<p><br/></p>
			<Share />
		</Content-Text>
		<FixedBackground text="住在貨櫃屋裡的女孩" :src="pic1_mobile"/>
		<ContentText>
			<Quote text="檳榔攤的阿姨問她：「媽媽呢？」「媽媽跑了。」" color="#FF4612" borderColor="#B5B5B5"/>
			<p><br/></p>
			<p><br/></p>
			<p>人們發現她的時候還沒上小學，除了這句話，她怕生不說話，對人充滿警戒，面無表情，就像野生動物。</p>
			<p><br/></p>
			<p>路過西螺大橋的鄉民，好心幫爸爸介紹工作，讓他有收入，勉強可以租個房子安頓女兒，但卻因為衛生習慣不佳，把房子弄得太髒亂遭房東趕出去。雇主楊金元把用來當倉庫的貨櫃屋清出來，讓父女有個遮風避雨的地方。</p>
			<p><br/></p>
			<ImageContain width="720" height="580" :src="pic2_mobile" imgsay="圖說圖說圖說圖說"/>
			<p><br/></p>
			<p>「她爸爸來我這邊打工，我們每天六點就出門了，結果小孩常常沒上學，有時候6天沒上學、10天沒上學，情況很嚴重，老師找不到她爸爸，就打電話給我找小孩、校長也打給我、社會局也打給我，最後連少年組也打給我了！」楊大哥說，閒置的貨櫃屋剛好在學校正對面，也方便學校老師早上來帶孩子去上課。</p>
			<p><br/></p>
			<p><br/></p>
			<Quote text="但小女孩不會洗澡，也不會洗衣服，因為貨櫃屋沒有浴室，也沒有晾衣服的地方，渾身異味導致其他孩子排斥她。" color="#FF4612" borderColor="#B5B5B5"/>
			<p><br/></p>
			<p><br/></p>
			<p>小女孩的班導師說，學校把校內的淋浴間整理出來給小女孩洗澡跟晾衣服，同學看他的眼光變友善，才能讓她融入群體。</p>
			<p><br/></p>
			<p>不只是洗澡問題，每天接她上課時，班導師總會看到貨櫃屋裡滿地的垃圾，連衣服襪子也丟在地上凌亂一團。楊大哥與班導師，一人盯爸爸、一人 漠然，得重新開始輔導。</p>
			<p><br/></p>
			<p>貨櫃屋原本一無長物，只有簡陋的鐵皮搭蓋，地上鋪著一個二手床墊讓父女睡覺，「我去問心理師該怎麼做，他說要能提供給孩子一個安全的環境，來學校比在家覺得安全。現在她覺得家裡比較安全，因為學校會有功課壓力，能不能透過情感的連結，強化到在學校是受關愛，可以安全學習。」</p>
			<p><br/></p>
			<p>課輔老師拜託合作課程的永齡教育基金會幫忙，協同台南市勞工局的志工隊，把貨櫃屋的環境改善，包括加裝隔熱、裝設衛浴設備，志工隊熱情迅速，很快地讓父女有可以安心洗熱水澡、洗衣服的地方。</p>
		</ContentText>
		<div id="cross-1" class="blank"></div>
		<div id="cross-2" class="blank"></div>
		<Hello />
		<canvas id="back" ></canvas>
		<canvas id="back2" ></canvas>
		<video id="video1" src="./assets/video1_mobile.mp4"/>
	</div>
</template>

<script>
import Hello from './components/Hello'
import Indicator from './components/Indicator'
import HeadBar from './components/HeadBar'
import Cover from './components/Cover'
import ContentText from './components/Content'
import Share from './components/Share'
import FixedBackground from './components/FixedBackground'
import Quote from './components/Quote'
import ImageContain from './components/ImageContain'

import pic1_mobile from './assets/mobile/pic1.jpg'
import pic2_mobile from './assets/mobile/pic2.jpg'
import pic3_mobile from './assets/mobile/pic3.jpg'
import pic4_mobile from './assets/mobile/pic4.jpg'

import bg_mobile from './assets/bg_mobile.jpg'

var canvas
var ctx
var canvas2
var ctx2
var counter
var video1
var t = new Image()
t.src = bg_mobile
var pic3

export default {
    name: 'app',
    data: function(){
    	return{
			pic1_mobile : pic1_mobile,
			pic2_mobile : pic2_mobile
    	}
    },
    mounted: function(){
		window.addEventListener('scroll', this.handleScroll)
		$('#back').prop('width', 375)
		$('#back').prop('height', 667)
		$('#back2').prop('width', 375)
		$('#back2').prop('height', 667)
		canvas = document.getElementById('back');
		ctx = canvas.getContext('2d');
		canvas2 = document.getElementById('back2');
		ctx2 = canvas2.getContext('2d');
		video1 = document.getElementById("video1"); 
		t.addEventListener('load', function(){
			ctx.drawImage(t, 0, 0, 720, 1280, 0, 0, 374, 666);
		}, false)
		pic3 = new Image()
		pic3.src= pic3_mobile

		FB.XFBML.parse()
    },
    methods: {
		handleScroll: function(event){
		let h = window.innerHeight
		let scroll_now = event.srcElement.body.scrollTop
		if(scroll_now < h * 3 / 4){
			video1.pause()
			clearInterval(counter)
			ctx.drawImage(t, 0, 0, 720, 1280, 0, 0, 374, 666);
			$('#back').css('visibility', 'visible')
			$('#back').css('opacity', 1)
			$('#back2').css('opacity', 0)
			$('#back2').css('visibility', 'hidden')
			console.log(2)
		}
		else if(scroll_now >= h * 3 / 4 && scroll_now < h * 7 / 4){
			video1.play()
			counter = setInterval(function(){
				ctx2.drawImage(video1, 0, 0, 374, 666, 0, 0, 374, 666)
			}, 100)
			$('#back').css('visibility', 'hidden')
			$('#back2').css('visibility', 'visible')
			$('#back').css('opacity', 0)
			$('#back2').css('opacity', 1)
			console.log(3)
		}
		else if(scroll_now >= h * 7 / 4 && scroll_now < $('#cross-1').offset().top - (h + 200)){
			video1.pause()
			clearInterval(counter)
			$('#back').css('visibility', 'hidden')
			$('#back2').css('visibility', 'hidden')
			$('#back').css('opacity', 0)
			$('#back2').css('opacity', 0)
			console.log(4)
		}
		else{
			$('#back').css('visibility', 'visible')
			$('#back').css('opacity', 1)
			ctx.drawImage(pic3, 0, 0, 720, 1280, 0, 0, 374, 666)
			console.log(5)
		}
      },
      drawMovie: function(){

      }
    },
    components: {
        Hello, HeadBar, Indicator, Cover, ContentText, Share, FixedBackground, Quote, ImageContain
    }
}
</script>

<style>
  
</style>