<script>
  export default {
    data() {
      
    }
  }
</script>

<template>
  <div class="service">
    <h1>Сервис прогноза погоды</h1>
    <p>Узнай погоду в своем городе</p>
    <input type="text" name="" id="">
    <button type="button">Узнать погоду</button>
  </div>
</template>

<style scoped>

  .service {
    color: white;
  }
  .service h1{
    text-align: center;
  }
  .service p {
    margin-top: 15px;
    text-align: center;
  }
  .service input{
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

  .service input:hover {
    cursor: pointer;
    border-bottom-color: rgb(235, 255, 122);
  }

  .service input:focus {
    cursor: auto;
    border-bottom-color: rgb(235, 255, 122);
  }

  .service button {
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

  .service button:hover {
    cursor: pointer;
    transform: scale(1.2) translateY(-3px);
  }
</style>
