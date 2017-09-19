<template>
    <div>
        <div class="image-contain" v-bind:style="{height: containHeight}">
            <img :src="src" />
        </div>
        <div class="img-say">{{imgsay}}</div>
    </div>
</template>

<script>
export default {
    name: 'imagecontain',
    props: ['width', 'height', 'src', 'imgsay'],
    data: function(){
        return{
            
        }
    },
    computed: {
        containHeight: function(){
            if(window.innerWidth < 768){
                return this.height * window.innerWidth / this.width + 'px'
            }
            else{
                return this.height * (window.innerWidth-200) / this.width + 'px'
            }
            
        }
    }
}
</script>

<style scoped>
    img{
        position: absolute;
        width: 100%;
        margin-left: -20px;
    }
    .img-say{
        font-size: 15px;
        color: gray;
        margin-top: 5px;
    }
    @media screen and (min-width: 768px) and (max-width: 1024px){
        img{
            width: calc(100% - 200px);
            margin-left: 0;
        }
    }
    @media screen and (min-width: 1025px){
        img{
            width: 800px;
        }
    }
</style>
