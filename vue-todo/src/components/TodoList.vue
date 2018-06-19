<template>
    <section>
        <transition-group name="list" tag="ul">
            <li v-for="(todoItem, index) in propsdata" :key="todoItem" class="shadow">
                <i class="checkBtn fa fa-check" aria-hidden="true"></i>
                {{ todoItem }}
                <button class="removeBtn" type="button" @click="removeTodo(todoItem, index)"><i class="fa fa-trash-alt" aria-hidden="true"></i></button>
            </li>
        </transition-group>
    </section>
</template>
<script>
export default {
    props: ['propsdata'],
    methods: {
        removeTodo(todoItem, index) {
            this.$emit('removeTodo', todoItem, index);
        }
    }
}
</script>

<style>
ul {list-style-type:none;margin-top:0;padding-left:0;text-align:left;}
li {display:flex;min-height:50px;height:50px;margin:0.5rem 0;padding:0 0.9rem;background:#fff;border-radius:5px;line-height:50px;}
.checkBtn {margin-right:5px;color:#62acde;line-height:45px;}
.removeBtn {width:40px;margin-left:auto;border:0;font-size:15px;color:#de4343;}
.list-item {display:inline-block;margin-right:10px;}
.list-move {transition:transform 1s;}
.list-enter-active, .list-leave-active {transition:all 1s;}
.list-enter, .list-leave-to {opacity:0;transform:translateY(30px);}
</style>