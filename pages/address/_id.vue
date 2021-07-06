<template>

  <section>
    <div class="w-screen items-center flex justify-center">
      <div class="container w-11/12 my-12 mx-auto  md:px-12">
        <div class="flex flex-wrap  ">

          <!-- card  -->
          <div v-for="(asset, index) in data" :key="index" class=" px-1 md:w-1/2  lg:px-4 lg:w-1/3">
            <article
              class=" rounded-xl shadow-lg  h-4/5 w-full flex flex-col justify-center items-center hover:shadow-2xl border-2 ">
              <img alt="Placeholder" class="block h-auto w-auto p-4 h-5/6 " :src="asset.image_url">
              <div class="text-black h-full border-t-4 w-full  rounded-lg flex items-center justify-between pr-3 pl-3">
                <h1 class="flex flex-col">
                  <p>{{asset.id}} </p>
                  <p class="">{{asset.name}}</p>
                </h1>
              </div>
            </article>
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
    components: {
      Hero
    },
    data() {
      return {
        asset: '',
        address: '',
        data: ''

      }
    },
    async mounted() {
      this.address = this.$route.params.id;
      this.baseUrl = window.location.href + this.address
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

</style>
