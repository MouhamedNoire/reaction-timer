<template>
        <h2>the score of your game is : {{ score }} ms</h2>
        <p class="rank">your rank : {{ rank }}</p>
</template>
<script>
export default {
    props: ['score'],
    data(){
        return{
         rank: null   
        }
    },
    mounted(){
        if (this.score < 200){
            this.rank = 'Godlike'
        } else if (this.score < 300){
            this.rank = 'Pro'
        } else if (this.score < 400){
            this.rank = 'Average'
        } else if (this.score < 500){
            this.rank = 'Noob'
        } else {
            this.rank = 'Turtle'
        }
    }
}
</script>
<style>
    .rank{
        font-size:1.4em;
        color: #0faf87;
        font-weight: bold;
    }
</style>