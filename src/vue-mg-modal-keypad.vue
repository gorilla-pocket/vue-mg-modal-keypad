<template>
<div>
    <input type="input" class="form-control modal-keypad" :class="inputClass" readonly v-model="val" @click="show">
    <modal-dialog :show="showModal" @close="showModal=false" hide-header hide-footer size="custom" :width="width">
        <template v-slot:body>
            <div class="keypad-container">
                <input type="input" class="form-control form-control-lg display" readonly v-model="temp_val">
                <keyboard v-model="temp_val" :layouts="layouts" :maxlength="maxlength" @ok="ok" ></keyboard>
            </div>
        </template>
    </modal-dialog>
</div>
</template>

<script>
import Keyboard from './keyboard.vue'
import ModalDialog from 'vue-mg-modal-dialog'
export default {
    props: {
        value: {
            default: '',
        },
        maxlength: {
            default: 10,
        },
        layouts: {
            default: '123|456|789|0-{del:backspace}|{ok:ok}',
        },
        inputClass: {
            default: '',
        },
        width: {
            default: '350px',
        }
    },
    data() {
        return {
            showModal: false,
            val: '',
            temp_val: '',
        }
    },
    mounted() {
        this.val = this.value ? String(this.value) : ''
    },
    watch: {
        value() {
            this.val = this.value ? String(this.value) : ''
        },
    },
    methods: {
        show() {
            this.temp_val = ''
            this.showModal = true
        },
        ok() {
            this.val = this.temp_val
            this.$emit('input', this.val)
            this.showModal = false
        }
    },
    components: {
        Keyboard,
        ModalDialog,
    }
}
</script>

<style scope>
.keypad-container {
    font-size: 2rem;
}
.display {
    background-color: white !important;
    margin-bottom: .5rem;
}
.vue-keyboard-key {
    width: 5rem;
}
.modal-keypad {
    cursor: pointer;
    background-color: white !important;
}
</style>