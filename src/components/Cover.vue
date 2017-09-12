<template>
    <div id="cover" v-bind:style="{backgroundImage: 'url(\'' + test() + '\')'}">
        <h1>{{title}}</h1>
    </div>
</template>

<script>
export default {
    name: 'cover',
    props: ['bg', 'bgmobile', 'title'],
    methods: {
        test: function(){
            if(window.innerWidth <= 1024){
                return this.bgmobile
            }
            else{
                return this.bg
            }
        }
    }
}
</script>

<style scoped>
    #cover {
        height: 100vh;
        background-position: center center;
        background-repeat: no-repeat;
        background-size: cover;
    }
    h1{
        font-size: 40px;
        letter-spacing: -1px;
        color: #FFFFFF;
        line-height: 1.1;
        text-shadow: 0px 3px 7px rgba(0, 0, 0, 0.21);
        position: absolute;
        margin: 0;
    }
</style>
