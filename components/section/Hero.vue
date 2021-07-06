<template>
  
</template>

<script>
  export default {
    data() {
      return {
        address: '',
      }
    },
    methods: {
      copyTestingCode() {
        let testingCodeToCopy = document.querySelector('#testing-code')
        testingCodeToCopy.setAttribute('type', 'text')
        testingCodeToCopy.select()

        try {
          var successful = document.execCommand('copy');
          var msg = successful ? 'successful' : 'unsuccessful';
        } catch (err) {}

        /* unselect the range */
        testingCodeToCopy.setAttribute('type', 'hidden')
        window.getSelection().removeAllRanges()
      },
    },
    mounted() {
      this.address = this.$route.params.id;

    },

  }

</script>

<style>



</style>
