<template>
  <div class="block" v-if="showBlock" @click="stopTimer">
    hi there! {{displayTime}}
  </div>
  <!-- <p>Result : {{score}}</p> -->
</template>

<script>
export default {

    props:["displayTime"],

    data(){
        return{
            showBlock: false,
            score: 0,
            timer: null,
        }
    },

    mounted(){
        setTimeout(() => {
            this.showBlock =true;
            this.startTimer();
        }, this.displayTime)
    },

    // updated(){
    //     console.log("data updated");
    // },

    // unmounted(){
    //     console.log("unmounted");
    // },
    methods:{
        startTimer(){
           this.timer = setInterval(() => {
                this.score += 50;
            },50)
        },
        stopTimer(){
            clearInterval(this.timer);
            // console.log(this.score);
            this.$emit("endGame",this.score);
            // this.showBlock = false;
        }
    }

}
</script>

<style>
.block{
    width: 400px;
    height: 200px;
    display: flex;
    justify-content: center;
    align-items: center;
    margin: 20px auto;
    background-color: rgb(75, 188, 33);
    color: bisque;
    font-weight: bold;
    border-radius: 20px;
}
</style>