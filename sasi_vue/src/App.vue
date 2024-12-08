<template>
  <HikingTrailHeader/>
  <HikingTrailsDirectory :hikingList = hikingList />
</template>

<script>
  import HikingTrailHeader from "./components/HikingTrailHeader.vue";
  import HikingTrailsDirectory from "./components/HikingTrailsDirectory.vue";

  export default{
    name: "App",
    components:{
      HikingTrailHeader,
      HikingTrailsDirectory
    },
    data(){
      return{
        hikingList:[]
      }
    },
    methods:{
      async getHikingList(){
        const res = await fetch("https://hiking-trails-guide.onrender.com/api");
        const hikingData = await res.json();
        return hikingData[0].hiking;
      }
    },
    async created(){
        this.hikingList = await this.getHikingList();
    }
  }
</script>

<style scoped>
</style>