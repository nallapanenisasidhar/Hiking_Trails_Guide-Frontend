<template>
    <div class="hiking_card">
        <div class="hiking_photo">
            <img :src=hiking.hiking_trail_image alt=hiking.hiking_trail_name/>
        </div>
        <div class="hiking_details">
            <div class="hiking_container">
                <h3>{{hiking.hiking_trail_name}}</h3>
                <span class="pill" :style="{backgroundColor: this.getDifficultyColour(hiking.hiking_trail_difficulty)}"> {{hiking.hiking_trail_difficulty}} </span>
            </div>
            <p> <b>{{hiking.hiking_trail_description}}</b></p>
            <StarRatings :read-only="true" :rating="hiking.hiking_trail_rating" :star-size="20" active-color="gold"/>
            <p id="location"><img src="https://img.icons8.com/?size=20&id=85149&format=png" alt="Location Icon"/>{{hiking.hiking_trail_location}}</p>
            <p> {{hiking.hiking_trail_length}}</p>
        </div>
    </div>
</template>

<script>
    import StarRatings from "vue3-star-ratings";
    export default{
        name:"HikingTrail",
        components:{
            StarRatings
        },
        props:{
            hiking: Object
        },
        methods:{
            getDifficultyColour(difficulty){
                if(difficulty === "Easy") return "green"
                else if(difficulty=== "Moderate") return "orange"
                else return "tomato"   
            }
        }
    }
</script>

<style>
    div{
        font-family: "Lora", serif;
        font-weight: 500;
    }
    .hiking_card{
        display:flex;
        justify-content:left;
        align-items:center;
        border:transparent;
        border-radius:4px;
        padding:1em;
        margin:1em;
        box-shadow:0 4px 8px 0 rgba(0,0,0,0.2), 0 6px 20px 0 rgba(0,0,0,0.19);
    }
    .hiking_photo img{
        width:300px;
        height:300px;
        border: transparent;
        border-radius: 5px;
        margin-right: 50px;
    }
    .hiking_container{
        display: flex;
        justify-content:space-between;
        align-items:center;
    }
    .pill{
        border:transparent;
        border-radius: 4px;
        padding:5px;
        color:white;
    }
    .icons{
        width:30px;
        height:30px;
    }
    #location img{
        vertical-align:middle;
    }
</style>