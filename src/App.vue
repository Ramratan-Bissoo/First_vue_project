<template>
 <div>
   <Header/>  
   <div class="container">
   <router-view/>
   </div>
 </div>
 
</template>

<script>
import Header from '@/components/Header.vue'
export default {
  
  
  components:{
    Header
  }
 
  
}
</script>

<style>
 body{
   background: #222832;
 }
 .container{
   max-width: 900px;
 }
 .card{
   background: #1a1d24;
  }
 .card-body{
   color: #f9ffee;
 } 
 .card-body a{
   color: #efbb25;
 }
  


</style>
