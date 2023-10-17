<!-- eslint-disable vue/no-export-in-script-setup -->
<script>

export default {
  data () {
    return {
      toDoList: [
        {
          name:'first',
          status: 'incomplete'
        }
      ],
      newVal: ''
    }
  },
  methods: {
   add () {
    var item = {
      name: this.newVal,
      status: 'incomplete'
    }
    if(this.newVal.length){
      this.toDoList = [...this.toDoList, item]
    }  
    
   },

   deleteItem (index) {
      this.toDoList.splice(index,1)
   },

   markAsComplete (index){
     this.toDoList[index].status = 'complete'
   },

  handleInput (val) {
    this.newVal=val.target.value;
  }

  } 
}

</script>

<template>
  <div class="about">
    <h1>This is a To Do List </h1>
    <div v-for="(item, index) in toDoList" :key="item">
      <span :class="item.status === 'complete' && 'completedClass' " 
       @click="markAsComplete(index)">{{index + 1}} - {{ item.name }} 
      </span> 
       <button  @click="deleteItem(index)">Delete</button>
    </div>
    
    <input name='list' id='list' @input="handleInput"/>
    <button @click='add'>Add</button>
  </div>
</template>

<style>
@media (min-width: 1024px) {
  .about {
    min-height: 100vh;
    align-items: center;
  }
  li {
  background: #cce5ff;
  color: darkblue;
  margin: 5px;
  }
  .completedClass{
      text-decoration: line-through
  }
}
</style>
