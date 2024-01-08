<template>
    <div class="sidebar">
        <div class="active">
           <Film></Film>
            <span>My recordings</span>
        </div>

        <div >
            <Share></Share>
            <span>Requested</span>
        </div>
    </div>
</template>

<script setup>
import Film from '@/components/icons/film.vue';
import Share from '@/components/icons/share.vue';

</script>
