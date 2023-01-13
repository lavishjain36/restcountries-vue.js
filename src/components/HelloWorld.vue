<template>
  <div>
  <div class="hello" v-if="loading">Loading...</div>
  <div  v-else-if="error">{{ error }}</div>
  <div v-else>
  <table border="2">
      <thead>
        <tr>
          <th>Country</th>
          <th>Capital</th>
          <th>Currencies</th>
          <th>Language</th>
          <th>Population</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="country in countries" :key="country.name">
          <td>{{ country.name }}</td>
          <td>{{ country.capital }}</td>
           <td>
            <div v-for="currency in country.currencies" :key="currency.code">
              {{ currency.name}}-{{ currency.code }}
            </div> 
           </td>
           <td>
            <div v-for="language in country.languages" :key="language.code">
              {{ language.name }}
            </div>
           </td>
          
        </tr>
      </tbody>
    </table>
  </div>
</div>
</template>
<script>
import axios from "axios";
export default {
  name: 'HelloWorld',
  data(){
    return{
      countries:[],
    }
  },
  mounted(){
    axios.get('https://restcountries.com/v2/all')
    .then(response =>{
      this.countries = response.data;
      // console.log(response.data);
     
    }).catch(error=>{
      this.error = error.message;
    })
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

.hello{
  background-color: rgb(0, 255, 166);
}
.test{
  background-color: rgb(82, 232, 22);
  border: 2px solid  coral;
  width:400px;
  margin: auto;
}
</style>
