<template>
    <div class="inputBox shadow">
        <input type="text" v-model="newTodoItem" placeholder="Type what you have to do" v-on:keyup.enter="addTodo">
        <button v-on:click="addTodo" class="addContainer"><i class="addBtn fa fa-plus" aria-hidden="true"></i></button>

        <modal v-if="showModal" @close="showModal = false">
            <h3 slot="header">경고</h3>
            <span slot="body" @click="showModal = false">할일을 입력하세요. <i class="closeModalBtn fa fa-times" aria-hidden="true"></i></span>
        </modal>
    </div>
</template>
<script>
import Modal from './common/Modal.vue'

export default {
    data() {
        return {
            newTodoItem: '',
            showModal: false
        }
    },
    methods: {
        addTodo() {
            if (this.newTodoItem !== "") {
                var value = this.newTodoItem && this.newTodoItem.trim();
                this.$emit('addTodo', value);
                this.clearInput();
            } else {
                this.showModal = !this.showModal;
            }
        },
        clearInput() {
            this.newTodoItem = '';
        }
    },
    components: {
        Modal: Modal
    }
}
</script>

<style scoped>
input:focus {outline:none;}
.inputBox {display:flex;height:50px;background:#fff;border-radius:5px;line-height:50px;}
.inputBox input {border-style:none;font-size:0.9rem;text-align:center;}
.addContainer {display:inline-block;float:right;width:3rem;height:inherit;background:linear-gradient(to right, #6478fb, #8763fb);border-radius:0 5px 5px 0;border:0;}
.addBtn {color:#fff;vertical-align:middle;}
</style>