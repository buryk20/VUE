<template>
  <div>
    <button class="btn btn-primary" 
        v-on:click="showH2 = !showH2">
        {{ btnTexts }}
            Нажми меня
        </button>
        <hr>
        <transition name='slide'>
          <h2 v-show="showH2" class="alert alert-success"> Сумма чисел {{ sum }}</h2>
        </transition>   
        <hr>
        <hr>
        <button class="btn btn-success"
                v-on:click="addNumber"
                v-bind:disabled="done">
        Чистло
        </button>
    <hr>
    <ul class="list-group">
        <li class="list-group-item" v-for="number in numbers">
            {{ number }}
        </li>
    </ul>
  </div>        
</template>
<script>
  export default {
    data(){
      return {
        // counter: 0,
        showH2: true,
        numbers: [],
        maxNumbers: 10
      }
    },
    methods: {
        addNumber(){
            if (!this.done) {
                let rnd = Math.floor(Math.random() * 54) - 27;
                this.numbers.push(rnd);
            }
            
        },
    },
    computed: {
        sum() {
            let sum = 0;
            for (let i = 0; i < this.numbers.length; i++){
                sum += this.numbers[i];
            }
            return sum;
        },
        btnTexts(){
            return this.showH2 ? 'Изчезни' : 'Появись';
        },
        done() {
            return this.numbers.length >= this.maxNumbers;
        }
    }
  }
</script>
<style scoped>
  .conteiner {
    color: aqua;
  }
</style>
