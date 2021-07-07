<template>
<section>
    <div class='timer'>
        <div class='timer__text'>
        <h1 class='timer__text__title'>One Minute Timer {{emojiIcon}} </h1>
        <span class='timer__text__seconds'>{{minutes}}:{{seconds}} <span><i>{{text}}</i></span></span>     
    </div>

    <div class='timer__button'>
        <button  v-if="!screenTime" @click="start">Start</button>
        <button  v-if="screenTime" @click="stop">Stop</button>
        <button  v-if="isReset" @click="reset">Reset</button>
    </div>
    </div>
    
</section>
</template>

<script>
import {ref} from "vue"
export default {
    data() {
        return {
            screenTime: null,
            emojiIcon: "⏰",
            totalTime: ref(1 * 60),
            isReset: true,
            text: 'minute'

        }
    },
    methods:{
            start() {
                
                this.screenTime = setInterval(()=>this.timerCountdown(), 1000);
               
            
            },
            stop() {
                clearInterval(this.screenTime);
                this.screenTime = null;
               
            },
            reset() {
                clearInterval(this.screenTime);
                this.totalTime = (1 * 60);
                this.text = 'minute'
                this.screenTime = null; 
                
            },
            editScreenTime(time) {
                return (time < 10 ? '0' : '') + time;  
            },
            timerCountdown() {
                this.totalTime--;
                if (this.totalTime == 0) {
                    this.reset()   
                }
                
                this.totalTime < 60 ? this.text = 'seconds' : ''
                this.totalTime >= 60 ? this.text = 'minute' : ''

            },
        },
         computed:{
            minutes() {
                return this.editScreenTime(Math.floor(this.totalTime / 60));
            },
            seconds() {
                return this.editScreenTime(this.totalTime - (this.minutes * 60));
            }
        }

}
</script>

<style lang="scss">

@import url("https://fonts.googleapis.com/css2?family=Work+Sans:wght@300;500&display=swap");

* {
  font-family: "Work Sans", sans-serif;
  margin: 0;
  padding: 0;
  background-color: #fff;
}
.timer {
  margin: auto;
  width: 50%;
  height: 30em;
  border: 4px dashed #aba7a2;
  padding: 20px;
  text-align: center;

  &__text {
    padding: 10%;

    &__title {
      font-weight: 500;
      font-size: 40px;
      margin: 35px;
      color: #333;
    }
    &__seconds {
      font-size: 60px;

      span {
        font-weight: 300;
        font-size: 25px;
        color: #aba7a2;
      }
    }
  }
  &__button {
    button {
      font-size: 25px;
      background-color: Transparent;
      background-repeat: no-repeat;
      border: none;
      cursor: pointer;
      overflow: hidden;
      outline: none;
      margin-right: 25px;
    }

    button:hover {
      border-bottom: 3px solid #e12929;
    }
  }
}



</style>