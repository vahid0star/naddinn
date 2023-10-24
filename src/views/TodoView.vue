<template>

    <Todo :Task="Task" :Status= "Status" :Edit="Edit" :Delete= "Delete" />
</template>
    
    <script>
    import Todo from "../components/ToodoView.vue";

        export default {
          components: {
            Todo
          },
          
          data() {
            return{
              Task: 'Task',  
              Status: 'Status', 
              Edit: 'Edit',  
              Delete: 'Delete'
                        
        }
        
      }
      
    } 
  
    </script>
    
