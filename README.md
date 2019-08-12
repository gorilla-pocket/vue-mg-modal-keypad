# vue-mg-modal-keypad

![npm](https://img.shields.io/npm/v/vue-mg-modal-keypad)
![npm](https://img.shields.io/npm/dm/vue-mg-modal-keypad)

## Installation

```
npm i vue-mg-modal-keypad
```

## Usage

app.js

```javascript
import ModalKeypad from 'vue-mg-modal-keypad'
Vue.component('ModalKeypad', ModalKeypad)
```

Example:

```html
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
import 'bootstrap'
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
```

## License

MIT