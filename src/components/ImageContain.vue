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
            return this.height * window.innerWidth / this.width + 'px'
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
</style>
