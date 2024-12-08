<template>
    <div v-for="hiking of hikingList" :key="hiking.hiking_trail_id">
        <HikingTrail :hiking = hiking />
    </div>
</template>

<script>
    import HikingTrail from "./HikingTrail.vue";

    export default{
        name:"HikingTrailsDirectory",
        components:{
            HikingTrail
        },
        props:{
            hikingList: Array
        }
    }
</script>

<style scoped>
</style>