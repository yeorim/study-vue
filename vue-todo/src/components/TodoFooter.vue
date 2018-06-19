<template>
    <div class="clearAllContainer">
        <button class="clearAllBtn" @click="clearTodo">Clear All</button>
    </div>
</template>
<script>
export default {
    methods: {
        clearTodo() {
            this.$emit('removeAll');
        }
    }
}
</script>

<style>
.clearAllContainer {width:8.5rem;height:50px;margin:0 auto;background:#fff;border-radius:5px;line-height:50px;}
.clearAllBtn {display:block;width:100%;height:100%;border:0;font-size:15px;color:#e20303;}
</style>