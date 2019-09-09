<template>
<div>
    <input type="input" class="form-control modal-keypad" readonly v-model="val" @click="show">
    <modal-dialog :show="showModal" @close="showModal=false" hide-header="true" hide-footer="true" size="custom" width="300px">
        <template v-slot:body>
            <div class="keypad-container">
                <input type="input" class="form-control form-control-lg display" readonly v-model="val">
                <keyboard v-model="val" :layouts="layouts" :maxlength="maxlength" @ok="ok" ></keyboard>
            </div>
        </template>
    </modal-dialog>
</div>
</template>

<script>
import keyboard from './keyboard'
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
        }
    },
    data () {
        return {
            showModal: false,
            val: '',
        }
    },
    mounted: function () {
        this.val = this.value ? String(this.value) : ''
    },
    watch: {
        value: function () {
            this.val = this.value ? String(this.value) : ''
        },
        val: function () {
            this.onInput()
        },
    },
    methods: {
        show: function () {
            this.showModal = true
        },
        onInput: function () {
            // console.log(this.val)
            this.$emit('input', this.val)
        },
        ok: function () {
            this.showModal = false
        }
    },
    components: {
        keyboard,
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