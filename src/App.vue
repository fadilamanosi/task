
<template>
  <Header></Header>
  <div class="main-divider">
    <Sidebar></Sidebar>
    <Main></Main>
  </div>
</template>



<script setup >
import Main from '@/components/main.vue';
import Header from '@/components/header.vue';
import Sidebar from '@/components/sidebar.vue';
</script>