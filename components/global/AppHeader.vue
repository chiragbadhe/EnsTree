<template>
  <div class=" flex w-screen justify-center  border bg-white h-16 md:h-24" >
    <div class="items-center flex justify-center md:justify-between w-9/12">

      <!-- logo Section -->
      <nuxt-link class="flex items-center " to="/">
        <img class="h-10 w-12" src="../../assets/img/logo.svg" alt="">
        <div class="font-normal text-2xl tracking-widest">
          EnsTree
        </div>
      </nuxt-link>

      <!-- link Section -->
      <div class="space-x-4 cursor-pointer hidden md:block">
          <nuxt-link to="/">        <span class="font-normal text-xl tracking-widest hover:text-gray-300">Home</span>
</nuxt-link>
 <nuxt-link to="/about">        <span class="font-normal text-xl tracking-widest hover:text-gray-300">About</span>
</nuxt-link>         <nuxt-link to="/contact">        <span class="font-normal text-xl tracking-widest hover:text-gray-300">Contact</span>
</nuxt-link>
      </div>
      
    </div>

  </div>
</template>

<script>
  export default {

  }

</script>

<style>

</style>
