<template>
  <div>
    <HomeSection />
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

</style>


<script>
import HomeSection from '~/components/section/HomeSection.vue';
  export default {
    components: {HomeSection},
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
      notEmpty() {
        if (this.address) {
          this.isOpen = true
        } else {
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
