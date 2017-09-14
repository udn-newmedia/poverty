<template>
    <div class="container content">
        <slot></slot>
    </div>
</template>

<script>
export default {
    name: 'content'
}
</script>

<style scoped>
    
    p{
        font-size: 21px;
        margin: 0;
    }
    @media screen and (max-width: 767px){
        p{
            font-size: 18px;
            line-height: 32px;
        }
        .content{
            padding: 64px 20px;
        }
    }
    @media screen and (min-width: 768px) and (max-width: 1024px){
        p{
            font-size: 20px;
            line-height: 32px;
        }
        
    }
    
    
</style>
