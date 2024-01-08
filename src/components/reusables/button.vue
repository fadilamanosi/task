<template>
    <button :class="small ?? 'large'"
        :style="'background-color:' + background + ';' + ' border: 1px solid ' + background + ';' + ' color:' + text">
        <slot></slot>
    </button>
</template>

<script setup>
defineProps(['background', 'text', 'small', 'large'])
</script>

<style scoped lang="less" >
button {
    background-color: transparent;
    border: 1px solid gray;
    border-radius: 20px;
    padding: 10px 20px;
    text-transform: capitalize;
    cursor: pointer;
    display: flex;
    justify-content: center;
    gap: 6px;
    align-items: center;
    transition: filter 150ms linear;
}

button:disabled{
           filter: brightness(60%);
           cursor: not-allowed;
        }
</style>