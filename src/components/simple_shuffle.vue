<template>
    <div>
        <transition-group name='shuffle-div' class='flex_box'>
            <div class='box' v-for='all in arr' :key='all'>{{ all }}</div>
        </transition-group>
        <div class='button' @click='shuffler()'>Shuffle</div>
        <div class='button' @click='auto()' v-if='show'>Auto Shuffle</div>
        <div class='button' @click='stop()' v-else>Stop</div>
    </div>
</template>


<script>

const _ = require('lodash');

export default {
    name: "simple-shuffle",
    data(){
        return {
            arr: [],
            show: true,
            autoIn: null
        }
    },
    methods: {
        shuffler(){
        	this.arr =  _.shuffle(this.arr);
        },
        auto(){
        	this.shuffler();
        	this.autoIn = setInterval(()=>{
            	this.shuffler();
            },500);
            this.show = false;
        },
        stop(){
            clearInterval(this.autoIn);
            this.show = true;
        }
    },
    mounted(){
        for (let i=0; i<100; i++){
            this.arr.push(i);
        }
    }
}

</script>



<style scoped>

.shuffle-div-move{
	transition: 0.5s;
}

.button{
	margin:auto;
    margin-top: 30px; 
    display:block;
    border: 1px solid lightGrey;
    width: 10%;
    height: 3%;
    color: lightGrey;
    text-align: center;
}

.button:hover{
    color: lightGreen;
    border-color: greenYellow;
    animation-name: hov;
    animation-duration: 1s;
    animation-iteration-count: infinite;
    animation-direction: alternate;
}

@keyframes hov{
    0% {
        border-radius: 0;
        transform: scaleY(1);
    }
    25% {
        border-radius: 5px;
        transform: scaleY(1.1);
    }
    50% {
        border-radius: 10px;
        transform: scaleY(1.2);
    }
    75% {
        border-radius: 15px;
        transform: scaleY(1.3);
    }
    100% {
        border-radius: 20px;
        transform: scaleY(1.4);
    }
}

.flex_box{
	position: relative;
    display: flex;
    margin: auto;
    border: 1px solid white;
    flex-wrap: wrap;
    flex-direction: row;
    width: 380px;
    margin-top: 20px;
    box-shadow: 0 0 5px brown;
    justify-content: space-between;
    border-radius: 5px;
}

.box{
	box-sizing: border-box;
    width: 25px;
    height: 25px;
    border: 1px solid white;
    margin: 5px;
    color: greenYellow;
    text-align: center; 
    padding: 2px;
}


</style>