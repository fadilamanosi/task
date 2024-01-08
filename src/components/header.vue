<template>
    <header>
        <div class="logo">
            <!-- <img src="../assets/logo.svg"> -->
            <div class="box">
                <div class="inside"></div>
            </div>
            <span>Adilo</span>
        </div>


        <ul class="links">
            <li>Project</li>
            <li class="active">
                Tools & App
                <arrow-down></arrow-down>
            </li>
            <li>Channels</li>
            <li>Contacts</li>
            <li>Analytics</li>
            <li>Settings</li>
        </ul>

        <div class="user">
            <span>Help</span>
            <div class="mini-info">
                <img src="/images/user.jpg">
                <div>
                    <span class="name">Cody Fisher</span>
                    <span class="email">fadilamanosi@gmail.com</span>
                </div>
            </div>
        </div>
    </header>
</template>

<script setup>
import arrowDown from "@/components/icons/arrow-down.vue"

</script>