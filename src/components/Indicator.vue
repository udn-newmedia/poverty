<template>
    <div id="indicator" v-bind:style="{opacity: opacity}">
        <div id="indicator-bar" v-bind:style="{width: progress + '%', backgroundColor: color}"></div>
    </div>
</template>

<script>
export default {
    name: 'indicator',
    props: ['color', 'progress', 'opacity'],
}
</script>

<style scoped>
    #indicator {
        top: 0;
        left: 0;
        position: fixed;
        width: 100%;
        z-index: 9999;
        opacity: 0;
        transition: opacity 0.7s ease;
        background-color: #FFFFFF;
    }
    /* default bar color */
    #indicator-bar{
        background-color: #AA4444;
    }
    @media screen and (max-width: 1024px){
        #indicator {
            height: 6px;
        }
        #indicator-bar {
            height: 4px;
        }
    }
    @media screen and (min-width: 1025px){
        #indicator {
            height: 6px;
        }
        #indicator-bar {
            height: 4px;
        }
    }
    
</style>
