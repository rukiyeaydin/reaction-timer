<template>
    <p>Reaction time: {{ score }} ms</p>
    <p :class="rankClass">{{ rank }}</p>
</template>

<script>
export default{
    props: ['score'],
    data(){
        return{
            rank: null,   
        }
    },
    mounted(){
        if(this.score < 250){
            this.rank = "Godlike";
        } else if(this.score < 400){
            this.rank = "Rapid Reflexes";
        } else if(this.score < 600){
            this.rank = "Average";
        } else {
            this.rank = "Snail Pace..";
        }
    },
    computed: {
        rankClass() {
            if (this.score < 250) {
                return "godlike";
            } else if (this.score < 400) {
                return "rapid-reflexes";
            } else if (this.score < 600) {
                return "average";
            } else {
                return "snail-pace";
            }
        },
    },
}
</script>

<style scoped>
 
.godlike{
    color: gold;
}
.rapid-reflexes{
    color: green;
}
.average{
    color: blue;
}
.snail-pace{
    color: red;
}

</style>