<template>
  <div class="">
    <!-- MAin Home -->
    <div class=" h-screen w-screen flex items-center pt-36 md:pt-1  md:justify-center flex-col text-center">
      <div class="font-normal text-4xl md:text-6xl tracking-widest text-center">The Only Link For NFTs</div>
      <div class="font-light  text-xl md:text-3xl mt-4 md:mt-8">View All Collictables At One Place</div>
      <button
        class="bg-purple-600 text-xl font-medium  hover:bg-purple-700 rounded-3xl msdw-1/5 text-white py-1 px-6 md:py-4 md:px-6  ms:mt-12 mt-6">
        Get Started
      </button>
      <div class="font-base text-base mt-4">Create Links</div>
    </div>
    <div class="-mt-52 w-screen mb-24  flex  flex-col items-center justify-center ">
      <img class=" md:w-1/4  " src="../../assets/img/phone.svg" alt="">
      <div class="flex flex-col font-bold text-purple-500">
        <p>|</p>
        <p>|</p>
        <p>|</p>
      </div>
  
      <div class="flex  justify-center flex-col items-center space-y-4">
        <input v-model.trim="address" class="h-full w-64  border border p-2 border-purple-500 rounded-lg outline-none	" placeholder="type link here" type="text">
        <button @click="notEmpty" class="bg-purple-600 rounded-full px-4 hover:bg-purple-700 py-2 text-white">Generate Link</button>
        <span class="flex space-x-4 items-center" v-if="isOpen">
          <input class="w-64 overflow-x-scroll" id="copyLinkAddress" :value="link + address">
          <button @click.stop.prevent="copyLink()"><img src="../../assets/img/copy.svg" alt=""></button>
        </span>
      </div>
    </div>

    <!-- HERO1 -->
    <div id="#about" class="h-screen w-screen text-center flex flex-col space-y-12 md:space-y-0 md:flex-row">
      <div class="w-full h-full items-center flex flex-col justify-center">
        <div class="md:m-32 ">
          <div class="font-medium text-5xl ">Link to all your NFTs</div>
          <div class="font-normal text-2xl mt-8">Linktree is the launchpad to your latest video, article, recipe, tour,
            store, website, social post - everywhere you are online.</div>
        </div>
      </div>
      <div class="md:w-full md:h-full items-center flex justify-center">
        <img src="../../assets/img/image1.svg" alt=""> </div>
    </div>

    <!-- HERO2 -->
    <div id="" class="h-screen w-screen flex-col-reverse text-center flex flex-col space-y-12 md:space-y-0 md:flex-row">
      <div class="w-full h-full items-center flex justify-center">
        <img src="../../assets/img/image2.svg" alt=""> </div>
      <div class="w-full h-full items-center flex flex-col justify-center">
        <div class="md:m-32">
          <div class="font-medium text-5xl ">Easily managed</div>
          <div class="font-normal text-2xl mt-8">Creating a EnsTree takes seconds. Use our simple create link option to
            effortlessly showcase your content.</div>
        </div>
      </div>
    </div>

    <div id="" class="h-screen  w-screen text-center flex flex-col space-y-12 md:space-y-0 md:flex-row">
      <div class="w-full h-full items-center flex flex-col justify-center">
        <div class="md:m-32">
          <div class="font-medium text-5xl ">Safe, trusted, public</div>
          <div class="font-normal text-2xl mt-8">Privacy is non-negotiable. EnsTree doesn’t track any personal data on
            your visitors, so your EnsTree remains your place on the internet.</div>
        </div>
      </div>
      <div class="w-full h-full items-center flex justify-center">
        <img src="../../assets/img/image3.svg" alt=""> </div>
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

  export default {
    components: {},
    data() {
      return {
        isOpen: false,
        baseUrl: '',
        address: '',
        link: this.baseUrl + this.address,
      };
    },

    methods: {
      notEmpty() {
        if (this.address.length == 0) {
          swal("PLease Enter Address")
        }
        else {
          this.isOpen = true
        }
      },

      copyLink() {
        let testingCodeToCopy =  document.querySelector('#copyLinkAddress')
        testingCodeToCopy.setAttribute('type', 'text') // 不是 hidden 才能複製
        testingCodeToCopy.select()

        try {
          var successful = document.execCommand('copy');
          var msg = successful ? 'Successful' : 'Unsuccessful';
          swal('Link was Copied ' + msg);
        } catch (err) {
          swal({   dangerMode: true,
title: "Oops, unable to copy"});
        }
      },
    },

    async mounted() {
      this.baseUrl = window.location.href
      this.link = this.baseUrl + ''

    }
  }

</script>
