<template>
    <label class='box'>
        <input @click="get($event.target)" :checked="checked" type='checkbox' />
        <span class='background'>
            <span class='toggle'></span>
        </span>
    </label>
</template>

<script setup>
defineProps(['checked'])
const emits = defineEmits(['value']);

function get(e) {
    emits('value', e.checked)
}
</script>

<style scoped lang="less">
.box {
    position: relative;
    display: block;
    width: 40px;
    height: 20px;
    margin-top: 8px;
    cursor: pointer;
}

.box input[type=checkbox] {
    opacity: 0;
    position: absolute;
    width: 100%;
    height: 100%;
}

.box input[type=checkbox]+.background {
    position: absolute;
    width: 100%;
    height: 100%;
    background: #A3BBC6;
    transition: background 150ms linear;
    border-radius: 20px;

}

.box input[type=checkbox]:checked+.background {
    background: #08D688;
}

.box input[type=checkbox]+.background .toggle {
    display: block;
    position: absolute;
    content: '';
    background: #fff;
    width: 50%;
    height: 100%;
    transition: margin 150ms linear;
    border-radius: 30px;
    border: 2px solid #A3BBC6;

}

.box input[type=checkbox]:checked+.background .toggle {
    margin-left: 20px;
    border: 2px solid #08D688;
}

.box .label {
    display: block;
    position: absolute;
    width: 50%;
    color: #ddd;
    line-height: 80px;
    text-align: center;
    font-size: 15px;
}
</style>