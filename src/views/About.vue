<template>
  <div class="about">
    <h1> an about </h1>
  </div>
</template>
<style scoped>
h1{
  color: white;
  text-align: center;

}
h1::before{
  content: "This is ";
}
h1::after{
  content: " page";
  
}
</style>
