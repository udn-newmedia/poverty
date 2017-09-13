<template>
    <div id="cover">
        <div id="title-contain" v-bind:style="{top: titleTop + 'px', left: titleLeft + 'px', bottom: titleBottom + 'px', right: titleRight + 'px', width: titleWidth + 'px', height: titleHeight + 'px'}">
            <h1 v-html="title"></h1>
        </div>
    </div>
</template>

<script>
export default {
    name: 'cover',
    props: ['title', 'titleTop', 'titleLeft', 'titleRight', 'titleBottom', 'titleWidth', 'titleHeight'],
    computed: {
        test: function(){
            let temp = this.title.split('<br/>').map(function(item, key){
                return '<span>' + item + '<br/></span>'
            })
            console.log(temp)
            return temp
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
    #title-contain{
        position: absolute;
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
