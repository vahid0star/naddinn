<template>  
  <div>{{todayDate}}</div>
  <h2>{{ greet }}</h2>
  <div class=" flex flex-row justify-center">
  <div v-text="message">
  </div><h1 class="px-2">"{{$store.state.count}}"</h1></div>
  </template>

<script lang="ts">  
   import moment from 'moment'
   export default {    
       name: 'myComponent', 
       data () {  
           return {        
               todayDate: moment().format('H:MM'),
               message: greet
              }
            }   
          }
          var myDate = new Date();
          var hrs = myDate.getHours();
          var greet:string
          

   if (hrs < 12)
     greet = 'Good Morning';
   else if (hrs >= 12 && hrs <= 17)
     greet = 'Good Afternoon';
   else if (hrs >= 17 && hrs <= 24)
     greet = 'Good Evening';
   </script>