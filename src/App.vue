<template>
  <div id="app">
    <Indicator color="#000000" v-bind:progress="progress" v-bind:opacity="opacity" />
    <HeadBar v-bind:position="position" />
    <Cover v-bind:bg="bg" v-bind:bgmobile="bgmobile" title="123"/>
    <Hello />
  </div>
</template>

<script>
import Hello from './components/Hello'
import Indicator from './components/Indicator'
import HeadBar from './components/HeadBar'
import Cover from './components/Cover'

import bgmobile from './assets/bg_mobile.jpg'
import bg from './assets/bg.jpg'

export default {
    name: 'app',
    data: function(){
        return{
            progress: 0,
            opacity: 0,
            position: 0,
            bg: bg,
            bgmobile: bgmobile
        }
    },
    mounted: function () {
        window.addEventListener('scroll', this.handleScroll);
    },
    methods: {
        handleScroll: function(event){
            let currentH = event.srcElement.body.scrollTop
            let totalH = event.srcElement.body.clientHeight - window.innerHeight
            this.progress = ((currentH / totalH) * 100).toFixed(2)
            if(event.srcElement.body.scrollTop < window.innerHeight / 2){
                this.opacity = 0
                this.position = 0
            }
            else{
                this.opacity = 1
                this.position = 4
                console.log(5)
            }
        }
    },
    components: {
        Hello, HeadBar, Indicator, Cover
    }
}
</script>
