<template>
  <div>

       <div class="h-screen  flex  flex-col items-center justify-center ">
         <img class="h-4/6	 " src="../assets/img/iphone.png" alt="">
          <div class="relative h-16 w-1/3 border-4 p-1 border-red-500 text-xl font bold rounded-3xl flex items-center justify-center m-2">

          <h1 class="pr-0.5">{{link}}</h1>
           <input v-model="address" class="h-full w-1/2 rounded-3xl outlixne-none	" placeholder="type link here" type="text">
           <a @click="notEmpty()"  target="_blank" class=" bg-indigo-900 rounded-full px-4 hover:bg-indigo-800 py-2 text-white" :href="link + address">></a>
        </div>
       </div>
      </div> 

</template>


<script>
  export default {
  components: {  },
    data() {
      return {
        isOpen: false,
        baseUrl: '',
        address: '',
        link: this.baseUrl + this.address,
        test: ''
      };
    },

    methods: {
      notEmpty(){
        if(this.address) {
          this.isOpen = true
        }
        else{
          this.alert("PLease Enter Address")
        }
      },
    },

    async mounted() {
      this.baseUrl = window.location.href
      this.link = this.baseUrl + 'address/'

    }
  }

</script>
