<template>
  <div class="">
    <!-- MAin Home -->
    <div class="h-screen md:-mt-36 w-screen flex items-center pt-36 md:pt-1  md:justify-center flex-col text-center">
      <div class="font-normal text-4xl md:text-6xl tracking-widest text-center">The Only Link For NFTs</div>
      <div class="font-light  text-xl md:text-3xl mt-4 md:mt-8">View All Collictables At One Place</div>
      <button @click="goto('createLink')"
        class="bg-purple-600 text-xl font-medium  hover:bg-purple-700 rounded-3xl md:w-1/5 text-white py-1 px-6 md:py-4 md:px-6  ms:mt-12 mt-6">
        Get Started
      </button>
    </div>

    <div ref="createLink" class=" w-screen mb-24 h-screen flex flex-col items-center justify-center ">
      <img class=" md:w-1/4 " src="../../assets/img/phone.svg" alt="">
      <div class="flex flex-col font-bold text-purple-500">
        <p>|</p>
        <p>|</p>
        <p>|</p>
      </div>

      <div class="flex  justify-center mb-96 flex-col items-center  md:w-screen">
        <input v-model.trim="address"
          class=" rounded-full px-4 w-72 py-2 md:p-6 md:w-1/2 md:text-2xl  outline-none border-2 border-purple-500	"
          placeholder="Your Ethereum Address" type="text">
        <button @click="notEmpty()"
          class="bg-purple-600 md:mt-6 mt-4 rounded-full px-4 hover:bg-purple-700 py-2 md:p-6 md:w-96 md:text-2xl text-white">Generate
          Link</button>
        <span class="flex space-x-4 items-center md:mt-8 mt-4" v-if="isOpen">
          <input class="md:w-96 w-36 overflow-x-scroll md:text-2xl " id="copyLinkAddress" :value="link + address">
          <button @click.stop.prevent="copyLink()"><img src="../../assets/img/copy.svg" alt=""></button>
        </span>
      </div>
    </div>
  </div>
</template>

<style>
  @import url('https://fonts.googleapis.com/css2?family=Nunito:wght@300&display=swap');

  * {
    margin: 0px;
    padding: 0px;
  }

  body {
    font-family: 'Nunito', sans-serif;
  }


  .swal-button--confirm {
    background: #6D28D9;
  }

</style>


<script>
  import swal from 'sweetalert';
  import AppHeader from '~/components/global/AppHeader.vue'

  export default {
    components: {
      AppHeader
    },
    data() {
      return {
        isOpen: false,
        baseUrl: '',
        address: '',
        link: this.baseUrl + this.address,
      };
    },

    methods: {
      goto(refName) {
        var element = this.$refs[refName];
        var top = element.offsetTop;

        window.scrollTo(0, top);
      },


      notEmpty() {
        var WAValidator = require('wallet-address-validator');
        var valid = WAValidator.validate(this.address, 'ethereum');
        if (valid)
          this.isOpen = true
        else
          swal(
            'Oops...',
            'Enter Valid A!',
            'error'
          )

      },

      copyLink() {
        let testingCodeToCopy = document.querySelector('#copyLinkAddress')
        testingCodeToCopy.setAttribute('type', 'text') // 不是 hidden 才能複製
        testingCodeToCopy.select()

        try {
          var successful = document.execCommand('copy');
          swal({
            title: "Good job!",
            text: "Link Copied!",
            icon: "success",
            button: "Close",
          });
        } catch (err) {
          swal({
            dangerMode: true,
            title: "Oops, unable to copy"
          });
        }
      },
    },

    async mounted() {
      this.baseUrl = window.location.href
      this.link = this.baseUrl + ''

    }
  }

</script>
