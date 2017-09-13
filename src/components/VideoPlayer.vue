<template>
    <div class="video-contain">
        <video v-bind:src="src" v-on:click="videoClick"/>
    </div>
</template>

<script>

export default {
    name: 'videoPlayer',
    props: ['src'],
    methods: {
        videoClick: function(){
            console.log(5)
            this.$el.children[0].play()
            console.log(this)
        }
    }
}
</script>

<style scoped>
    video{
        width: 100%;
        height: 100vh;
    }
</style>
