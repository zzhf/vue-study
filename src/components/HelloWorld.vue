<template>
  <dc-button>{{ msg }}</dc-button>
</template>

<script>
import DcButton from './../base/components/BaseButton';

export default {
  name: 'HelloWorld',
  components: {
    DcButton
  },
  data () {
    return {
      msg: 'Welcome to Your Vue.js App'
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
</style>
