<template>
<div class="hello">
  <form action="" @submit.prevent="onSubmit">
    <label for="name">Name:</label>
    <input type="text" id="name" v-model="name" required/>
    <br/> <br>
    <label for="email">Email:</label>
    <input type="email" id="email" v-model="email" required/>
    <br/> <br/>
    <label for="product">Product:</label>
    <select name="product" id="product" v-model="product" required>
    <option v-for="p in products" :key="p.id" :value="p.id">
    {{ p.name }}
    </option>
    </select>
    <br/><br/> <br/>
    <label for="quantity">Quantity:</label>
    <input type="number" id="quntity" v-model.number="quantity" required/>
    <br><br/> <br/>
    <button type="submit">Checkout</button>
  </form>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  data(){
    return{
      name:'',
      email:'',
      product:'',
      quantity:0,
      products:[
        {id:1,name:"product1"},
        {id:2,name:"product2"},
        {id:3,name:"product3"},
        {id:4,name:"product4"},
        {id:5,name:"product5"}
      ]
    }
  },
  methods:{
    onSubmit(){
      //logic to submit the form data display in console
      console.log(`
      Name: ${this.name}
      Email: ${this.email}
      Product: ${this.product}
      Quantity: ${this.quantity}
      `)
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
