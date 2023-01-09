<template>
<div class="hello">
   <form action="" @submit.prevent="addNote">
    <input type="text" v-model="newNoteText">
    <button type="submit">Add Note</button>
  </form>
  <ul>
    <li v-for="(note,index) in notes" :key="index">
     {{ note }}
      <button @click="removeNote(index)">X</button>
    </li>

  </ul>
 
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
      newNoteText:'',
      notes:[]
    }
  },
  methods:{
    addNote(){
      this.notes.push(this.newNoteText);
      this.newNoteText="";//input box empty 
    },
    removeNote(index){
      this.notes.splice(index,1);
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
