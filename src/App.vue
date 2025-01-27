<template>
  <div class="container">
    <listasRestrictivas/>
  </div>
</template>

<script setup>
  import listasRestrictivas from './components/listasRestrictivas.vue';

</script>

<style>
  :root{
    --color-fondo-n : #FFFFFF;
  }
  body{
    margin-top: 60px;
    display: flex;
    justify-content: space-evenly;
    background: var(--color-fondo-n);
    font-family: 'Anton', sans-serif;
    user-select: none;
    overflow: hidden;
    height: 100vh;
  }
  .container{
    display: flex;
    justify-content: center;
  }
  

</style>
