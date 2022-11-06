<template>
  <h2>My Course Goal</h2>
  <p>{{ myGoal }}</p>
  <input v-if="myGoal.length === 0" type="text" v-on:keydown.enter="AddmyGoal" />
  <!-- Task 1: Output your main course goal with help of the composition API -->
  <!-- Don't hardcode it into the template, instead hardcode it into the JS code -->
  <h3>OUTPUT COURSE GOAL</h3>
  <!-- Task 2: Toggle (show/ hide) the goal with help of the button  -->
  <p v-if="toggle">{{ myGoal }}</p>
  <button v-on:click="toggle =! toggle">Toggle Goal</button>
  <!-- Task 3: Manage data in three ways -->
  <!-- => Separate refs -->
  <!-- => Ref Object -->
  <!-- => Reactive Object -->
  <!-- Task 4: Also solve the assignment with the Options API -->
</template>

<script>
import { ref,reactive,watch } from 'vue';

export default {
  setup() {
    
    const myGoal = ref('');
    const myObj = reactive(
      {
      Goal:''
      }
    );

    const toggle = ref(true);


    function AddmyGoal(event){
      myGoal.value = event.target.value;
    }
    
    watch(myGoal,function(val){
      myObj.Goal = val;
      console.log(myObj);
    });
      
    
    


    return {myGoal,AddmyGoal,toggle}

  }
}
</script>

<style>
html {
  font-family: sans-serif;
}
body {
  margin: 3rem;
  text-align: center;
}
</style>