<template>
  <div>
      <input type="text" v-model="addToDolist">
      <button @click = 'saveToArray()' :class="hide">Add</button>
      <ul>
        <li v-for="(item, i) in toDoList" :key="i" >
          
        {{item}}<button @click = 'remove(i)'>Remove</button></li>
        
      </ul>
  </div>
</template>

<script>


export default {
  name: 'App',
  data(){
    return{
      counter: 0,
      toDoList : [],
      addToDolist: ""
    }
  },
//Цю штуку ЗЛИЗАВ зрозумів, що вона змінює ім я классу і як той клас
//потім змінюється в стилі. Але чого він його змінює і що куди повертає
//не дуже зрозумів
  computed:{
    hide(){
      return this.toDoList.length >= 10 ? 'hidden':''
    }
    
  },

  methods: { 
    saveToArray(){
      this.toDoList.push(this.addToDolist)
      this.addToDolist = ""
      console.log(this.toDoList.length)
    },
    remove(index){
      this.toDoList.splice(index,1)
    }
            
  }
} 
</script>

<style>
.hidden{
  display: none;
}
li{
  list-style-type: none
}
</style>
