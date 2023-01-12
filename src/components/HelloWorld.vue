<template>
<div class="hello">
  <form action="" @submit.prevent="getWeather">
    <label for="">Latitude:</label>
    <input type="text" v-model="latitude" id="latitude" required>
   <br>
   <label for="">Longitude</label>
   <input type="text" v-model="longitude" id="longitude" required>
   <br>
   <button type="submit">Get weather</button>
  </form>
  <div v-if="weather">
    <p>Temprature:{{ weather.main.temp }}</p>
    <p>weather:{{ weather.weather[0].main }}</p>
    <p>Wind Speed:{{ weather.wind.speed }}</p>
  </div>
</div>  

</template>

<script>

export default {
  name: 'HelloWorld',
  data(){
    return{
      latitude:'',
      longitude:'',
      weather:null
    }
  },
  methods:{
    async getWeather(){
      const url=`https://api.openweathermap.org/data/2.5/weather?lat=${this.latitude}&lon=${this.longitude}&appid=9bf59c67c0d408cc5e1c4877f3e4d9d5`;
      try{
        const response=await fetch(url);
        const data=await response.json();
        console.log(data);
        this.weather=data;
      }catch(error) {
        console.log(error);
    }
  }
}
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
