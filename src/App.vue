<template>
  <div id="app">
    <Indicator color="#000000" />
    <HeadBar />
    <Cover title="貧窮世襲<br />被遺忘的孩子" title-bottom="65" title-left="40" title-width="270" title-height="95"/>
    <div class="blank"></div>
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

import bg_mobile from './assets/bg_mobile.jpg'

var canvas
var ctx
var canvas2
var ctx2
var counter
var video1
var t = new Image()
t.src = bg_mobile

export default {
    name: 'app',
    data: function(){
      return{
      
      }
    },
    mounted: function(){
      window.addEventListener('scroll', this.handleScroll)
      $('#back').prop('width', 374)
      $('#back').prop('height', 666)
      $('#back2').prop('width', 374)
      $('#back2').prop('height', 666)
      canvas = document.getElementById('back');
      ctx = canvas.getContext('2d');
      canvas2 = document.getElementById('back2');
      ctx2 = canvas2.getContext('2d');
      video1 = document.getElementById("video1"); 
      t.addEventListener('load', function(){
        ctx.drawImage(t, 0, 0, 720, 1280, 0, 0, 374, 666);
      }, false)
    },
    methods: {
      handleScroll: function(event){
        let h = window.innerHeight
        if(event.srcElement.body.scrollTop < h){
            console.log(1)
            video1.pause()
            clearInterval(counter)
            $('#back').css('visibility', 'visible')
            $('#back').css('opacity', 1)
            $('#back2').css('opacity', 0)
            $('#back2').css('visibility', 'hidden')
        }
        else if(event.srcElement.body.scrollTop >= h && event.srcElement.body.scrollTop < h * 3 / 2){
          console.log(2)
            video1.play()
            counter = setInterval(function(){
              ctx2.drawImage(video1, 0, 0, 374, 666, 0, 0, 374, 666)
            }, 100)
            $('#back').css('visibility', 'hidden')
            $('#back2').css('visibility', 'visible')
             $('#back').css('opacity', 0)
            $('#back2').css('opacity', 1)
        }
        else{
            video1.pause()
            clearInterval(counter)
        }
      },
      drawMovie: function(){

      }
    },
    components: {
        Hello, HeadBar, Indicator, Cover
    }
}
</script>

<style>
video{
  opacity: 0;
}
</style>