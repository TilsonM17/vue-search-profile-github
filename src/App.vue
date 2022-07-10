<template>
  <div class="container-fluid">
  <Navbar></Navbar>
  <FormRequest></FormRequest>
  </div>
</template> 

<script>

import Navbar from "./components/navbar.vue";
import FormRequest  from "./components/FormRequest.vue";

export default {
  name: 'App',
  components:{
    Navbar,
    FormRequest,
},mounted(){
  
  }

 
}
</script>

<style>

</style>
