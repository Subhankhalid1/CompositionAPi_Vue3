<template>
  <div class="about">
    <!-- <input type="text" v-model="name"/>
    <h1>This is an about page name is {{ name }} and age is{{ age }}</h1>
    <button @click="handleClick">Updated</button>
    <button @click="age++">Add age By 1</button>
    <p>{{myName.age  }}</p>
    <button @click="reactiveUpdate">Update with Reactive</button> -->
<div>
  <input type="text" v-model="search"/>
  <div>
    <h3 v-for="item in matchingNames" :key="item">{{ item }}</h3>
  </div>
</div>
  </div>
</template>
<script>
import { ref, reactive, computed, watch, watchEffect } from 'vue';
export default{
name:"About",
  setup(){
    // const name=ref("")
    // const age=ref(23)
    // const myName=reactive({name:"ali", age:32})

    const names=ref(["subhan", "ali","ahmad", "zeeshan", "xyz","qwerty"])
   const search=ref('')


    // const handleClick=()=>{
    //   name.value="Rana"
    //   age.value=24
    // }
    // const reactiveUpdate=()=>{
    //   myName.age=25
    // }

    const matchingNames=computed(()=>{
      return names.value.filter((item)=>item.includes(search.value))
    })
      watch(search,()=>{
        console.log("watch function run")
      })

      watchEffect(()=>{
        console.log("watchEffect function run", search.value)
      })
    return{search, matchingNames, names}
  }
}
</script>

<style>

</style>