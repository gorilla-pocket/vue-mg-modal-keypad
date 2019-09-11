<template>
  <section class="container mt-2">
    <modal-keypad v-model="value" />
    <modal-keypad v-model="value2" layouts="123|456|789|0-.|{del:backspace}{ok:ok}" />
  </section>
</template>

<style lang="scss" scoped>
</style>

<script>
import ModalKeypad from '../src/vue-mg-modal-keypad'
import 'bootstrap/dist/css/bootstrap.min.css'
export default {
  data() {
    return {
      value: '',
      value2: '',
    }
  },
  methods: {
    ///
  },
  components: {
    ModalKeypad,
  },  
}
</script>