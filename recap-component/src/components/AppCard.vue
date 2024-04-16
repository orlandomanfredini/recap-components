<template>
    <strong>{{ nameCard }}</strong>
    <img :src="img" alt="">
    
</template>

<script>
    export default {
        props: {
            nameCard: String,
            img: String,
        },
        
    }
</script>

<style lang="scss" scoped>

</style>