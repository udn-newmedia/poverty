<template>
    <div class="fixed-background">
        <div class="canvas-bg" v-bind:style="{opacity: opacity}">
            <canvas />
        </div>
        <div class="fix-text">{{text}}</div>
    </div>
</template>

<script>

export default {
    name: 'fixedbackground',
    props: ['text', 'src'],
    data: function(){
        return{
            ctx: null,
            image: new Image(),
            opacity: 0
        }
    },
    methods: {
        drawCanvas:function(){
            this.ctx.drawImage(this.image, 0, 0, 720, 1280, 0, 0, 375, 667)
        },
        handleScroll: function(e){
            if(e.srcElement.body.scrollTop > (this.$el.offsetTop - window.innerHeight - 200) && e.srcElement.body.scrollTop < (this.$el.offsetTop + window.innerHeight)){
                this.opacity = 1
            }
            else{
                this.opacity = 0
            }
        }
    },
    mounted: function(){
        this.$el.children[0].children[0].width = 375
        this.$el.children[0].children[0].height = 667
        this.ctx = this.$el.children[0].children[0].getContext('2d')
        this.image.src = this.src
        this.image.addEventListener('load', this.drawCanvas)
        window.addEventListener('scroll', this.handleScroll)
    }
}
</script>

<style scoped>
    .fixed-background{
        height: 100vh;
        position: relative;
        display: flex;
        justify-content: center;
        align-items: center;
    }
    .fix-text{
        font-size: 26px;
        letter-spacing: -0.5px;
        color: #FFFEFE;
        text-shadow: 0px 3px 7px rgba(0, 0, 0, 0.4)
    }
    .canvas-bg{
        position: fixed;
        width: 100%;
        top: 0;
        left: 0;
        z-index: -1;
        transition: opacity 0.7s ease;
    }
    canvas{
        width: 100%;
    }
</style>
