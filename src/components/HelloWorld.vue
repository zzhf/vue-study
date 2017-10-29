<template>
    <dc-button>{{ msg }}</dc-button>
    <dc-alert>
        我是一个默认的弹出框
    </dc-alert>
</template>

<script>
import DcButton from './../base/components/BaseButton';
import DcAlert from './../base/components/Alert';

export default {
  name: 'HelloWorld',

  components: {
        DcButton, DcAlert
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
