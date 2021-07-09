<template>

  <section>

    <div class="w-screen hero items-center flex justify-center border-b-3 flex-col">
      <!-- Cover pHoto -->
      <div class="w-full bg-gradient-to-r from-purple-500 via-red-500 to-purple-500 backgroundinfo">

      </div>

      <!-- Image Profile -->
      <img class="h-44 w-42 absolute rounded-full bg-yellow-500"
        src="https://preview.keenthemes.com/metronic-v4/theme/assets/pages/media/profile/profile_user.jpg" alt="">


      <!-- description screen -->
      <div class="w-full flex flex-col backgroundinfo items-center border-b-2 flex justify-center pt-8">
        <h1 class="text-4xl font-bold ">profile.name</h1>
        <span class="text-base font-semibold mt-2 items-center flex space-x-3">
          <h1 class="w-36 overflow-x-scroll">{{address}}</h1> <img class="h-5" src="../assets/img/copy.svg" alt="">
        </span>
      </div>

    </div>
    <div class="w-screen items-center flex justify-center">
      <div class="container w-9/12 my-12 mx-auto ">
        <div class="grid md:grid-cols-3 md:grid-flow-auto md:gap-16 gap-8 ">
          <div v-for="(asset, index) in data" :key="index"
            class=" card  h-auto rounded-2xl justify-center items-center flex flex-col rounded-2xl shadow-lg hover:shadow-2xl border">

            <div class="h-4/5 rounded-t-2xl "> <img class="h-full rounded-t-2xl p-6" :src="asset.image_url" alt="">
            </div>
            <div class="cardinfo w-full w-auto pr-6 pl-6">
              <h1 class="flex flex-col">
                <p class="text-lg font-black	">{{asset.id}} </p>
                <p class="">{{asset.name}}</p>
              </h1>
            </div>

          </div>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
  export default {
    props: [
      'asset'
    ],
    components: {},
    data() {
      return {
        address: '',
        data: '',

      }
    },

    methods: {


    },
    async mounted() {

      this.address = this.$route.params.id;
      this.baseUrl = window.location.href + this.address


      const Box = require('3box')
      const profile = Box.getProfile(this.address)
      console.log(profile)


      const fetch = require('node-fetch');
      const url = 'https://api.opensea.io/api/v1/assets?owner=' + (this.address) +
        '&order_direction=desc&offset=0&limit=20';
      const options = {
        method: 'GET'
      };
      console.log(url)

      fetch(url, options)
        .then(res => res.json())
        .then(json => console.log(
          this.data = json.assets
        ))
        .catch(err => console.error('error:' + err));
    },
  }

</script>

<style>
  .card {
    height: 450px;
  }

  .cardinfo {
    height: 150px;

  }

  .hero {
    height: 450px;


  }

  .backgroundinfo {
    height: 225px;


  }

  .descinfo {
    height: 225px;


  }

</style>
