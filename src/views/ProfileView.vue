<template>
  <div  class="container flex-col items-center text-center justify-center" style="max-width: 600px;">
    <form @submit.prevent="addItem" class=" flex flex-row justify-content-center mt-5">
      <input v-model="$store.state.count" type="text" placeholder="name" 
      class="w-100 form-control">
      <a-button class=" bg-blue-500" type="primary">{{$store.state.button}} </a-button>      
    </form>
    <h1>{{ $store.state.count }}</h1>
    

    <div id="name" ></div>
    <select class=" my-10 text-4lg text-white bg-blue-700 hover:bg-blue-800 focus:ring-4 focus:ring-blue-300 font-medium rounded-lg px-5 py-2.5 mr-2 mb-2 dark:bg-blue-600 dark:hover:bg-blue-700 focus:outline-none dark:focus:ring-blue-800">
    <option  @click="updateCount">them</option>
    <option id="opt1">Daily</option>
    <option id="opt2">Weekly</option>
    <option id="opt3">Monthly</option>
    <option id="opt4">Annually</option>
  </select>
  <select class=" my-10 text-4lg text-white bg-blue-700 hover:bg-blue-800 focus:ring-4 focus:ring-blue-300 font-medium rounded-lg px-5 py-2.5 mr-2 mb-2 dark:bg-blue-600 dark:hover:bg-blue-700 focus:outline-none dark:focus:ring-blue-800">
    <option selected  @click="updateCount">local</option>
    <option id="opt1">tehran</option>
    <option id="opt2">mashhad</option>
    <option id="opt3">shiraz</option>
    <option id="opt4">yazd</option>
  </select>
  </div>
  <div
        
        v-for="(item1, i) in items1"
        :key="i"
        :value="item"
        >
  </div>


  </template>
  <script >
    import {ref} from 'vue'
    import {Button } from 'ant-design-vue';
      const pervCount = JSON.parse(localStorage.count || 0)
      const count = ref(pervCount)
  
      function updateCount(amount) {
        count.value = count.value + amount
        localStorage.setItem('count'.count.value)
      }
  
  export default ({
    
    props: {username:String,},
    
      components: {
      AButton: Button,
      
    },
    data() {
      // items1: [
      //   { text: 'پیراهن چهارخانه سبزآبی محوا' },
      //   { text: 'پیراهن چهارخانه قرمزسفید محوا' },
      //   { text: 'پیراهن چهارخانه سبزآبی محوا', },
      // ]  
              return {
                  newItem: '',
                  items: [],
              };
          },
          computed: {
              totalItems() {
                  return this.items.length;
              },
          },
          mounted() {
              
              // Load items from localStorage on component mount
              this.items = JSON.parse(localStorage.getItem('items')) || [];
          },
          
          methods: {
            
              addItem() {
                  this.items.push(this.newItem);
                  this.newItem = '';
                  localStorage.setItem('items', JSON.stringify(this.items));
              },
              removeItem(index) {
                  this.items.splice(index, 1);
                  localStorage.setItem('items', JSON.stringify(this.items));
              },
          },
  });
  
    
  </script>


<style>

</style>