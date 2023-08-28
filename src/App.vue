<script>

import axios from 'axios';

  export default {
    data() {
      return {
        city: "",
        error: "",
        info: null
    }
  },
  computed: {
    cityName() {
      return "«" + this.city + "»"
    },
    showTemp() {
      return "Температура: " + this.info.main.temp
    },
    showFeelsLike() {
      return "Ощущается, как: " + this.info.main.feels_like
    },
    showMinTemp() {
      return "Минимальная температура: " + this.info.main.temp_min
    },
    showMaxTemp() {
      return "Максимальная температура: " + this.info.main.temp_max
    }
  },
  methods: {
    getWeather() {
      if(this.city.trim().length < 2){
        this.error = "Некорректное название города";
        return false
      }
      this.error = "";

      /* axios.get(`https://api.openweathermap.org/data/2.5/weather?q=${this.city}&units=metric&appid=bf23ff8d54bb4889534894f131503597`)
        .then(res => {
          this.info = res.data
        }) */
    }
  }
}
</script>

<template>
  <div class="service">
    <h1 class="service__title">Сервис прогноза погоды</h1>
    <p class="service__text">Узнай погоду в {{ city == "" ? "своем городе" : cityName }}</p>
    <input class="service__input" type="text" v-model="city" placeholder="Введите название города">
    <button class="service__button" type="button" v-if="city != ''" v-on:click="getWeather()">Узнать погоду</button>
    <button class="service__button" disabled type="button" v-else>Нужно ввести название</button>
    <p class="service__text error">{{ error }}</p>
    <ul class="service__list" v-if="info != null">
      <li class="service__list-item">{{ showTemp }}</li>
      <li class="service__list-item">{{ showFeelsLike }}</li>
      <li class="service__list-item">{{ showMinTemp }}</li>
      <li class="service__list-item">{{ showMaxTemp }}</li>
    </ul>
  </div>
</template>

<style scoped>

  .service {
    color: white;
  }
  .service__title{
    text-align: center;
  }
  .service__text {
    margin-top: 15px;
    text-align: center;
  }
  .service__input{
    font-size: 16px;
    margin: 0 auto; 
    color: white;
    margin-top: 20px;
    max-width: 150px;
    display: block;
    text-decoration: none;
    border: 0;
    background-color: transparent;
    outline: none;
    border-bottom: 2px solid rgb(255, 255, 255);
  }

  .service__input:hover {
    cursor: pointer;
    border-bottom-color: rgb(235, 255, 122);
  }

  .service__input:focus {
    cursor: auto;
    border-bottom-color: rgb(235, 255, 122);
  }

  .service__button {
    display: block;
    margin: 20px auto 0;
    padding: 10px 12px;
    font-size: 16px;
    font-weight: 700;
    color: white;
    border: none;
    border-radius: 7px;
    background-color: rgba(191, 203, 127, 0.751);
    transition: transform ease-in 0.8s;
  }

  .service__button:hover {
    cursor: pointer;
    transform: scale(1.2) translateY(-3px);
  }

  .service__button:disabled {
    background-color: rgba(103, 109, 70, 0.751);
    cursor: not-allowed;
    transform: none;
  }

  .error{
    color: red;
    font-size: 16px;
    font-weight: 700;
  }

  .service__list {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    list-style-type: none;
  }

  .service__list-item{
    font-size: 16px;
    line-height: 1.5;
  }
  
</style>
