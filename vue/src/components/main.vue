<template>
    <section class="main">
        <div class="breadcumb">
            <span>
                snapbyte
            </span>
            <arrow-right></arrow-right>
            <span>
                My recordings
            </span>
        </div>

        <div class="header">
            <span class="mini">
                My recordings
                <b>{{ recordings.length }}</b>
            </span>

            <div class="buttons">
                <Button>
                    <arrow-disperse :text="'#637C8E'"></arrow-disperse>
                    By Date
                </Button>
                <Button>
                    <funnel :text="'#637C8E'"></funnel>
                    Add filter
                </Button>
                <Button :background="'#0CABD8'" :text="'white'">
                    <camera></camera>
                    new request
                </Button>
                <Button @click="record.options = true" :background="'#F05350'" :text="'white'">
                    <record-icon></record-icon>
                    start recording
                </Button>
            </div>
        </div>

        <div class="table">

            <div v-if="load" class="loader">
                <loader></loader>
            </div>

            <table v-else>
                <thead>
                    <tr>
                        <th>recordings</th>
                        <th>title</th>
                        <th>views</th>
                        <th>size</th>
                        <th>last modified</th>
                        <th></th>
                    </tr>
                </thead>
                <tbody>

                    <tr v-for="(item, index) in recordings" :key="index">
                        <td class="media">
                            <div class="box">
                                <label>{{ item.length }}</label>
                                <img :src="item.src" alt="">
                            </div>
                        </td>
                        <td class="info ">
                            <b>{{ item.title }}</b>
                            <span
                                v-html="item.description.length > 0 ? item.description : 'The Video description is shown here if the user has added it.'"></span>
                        </td>
                        <td>{{ item.views }}</td>
                        <td>{{ item.size }}</td>
                        <td>{{ item.last_modified }}</td>
                        <td>
                            <Option></Option>
                        </td>
                    </tr>


                </tbody>
            </table>
        </div>

    </section>

    <record-vue v-if="record.options" @close="record.options = false" @record="startRecording($event)"></record-vue>
    <recording v-if="record.start" :config="record.config"></recording>
</template>

<script setup>
import { computed, onMounted, ref } from "vue";
import axios from "axios";

// Reusables
import Button from "@/components/reusables/button.vue"
import recordVue from "@/components/modals/record.vue"
import recording from "@/components/modals/recording.vue"


import { data } from '../recordings';
import ArrowRight from "@/components/icons/arrow-right.vue";
import arrowDisperse from "@/components/icons/arrow-disperse.vue";
import funnel from "@/components/icons/funnel.vue";
import camera from "@/components/icons/camera.vue";
import recordIcon from "@/components/icons/record.vue";
import Option from "@/components/icons/option.vue";
import loader from "@/components/icons/loader.vue";


const recordings = ref({});
const load = ref(false)

function getRecordings() {
    load.value = true;
    axios.get('https://test.fadilamanosi.com/api/recordings')
        .then((e) => {
            recordings.value = e.data
            load.value = false;
        })
        .catch((e) => {
            console.log(e)
            load.value = false;
        })
}

const record = ref({
    options: false,
    start: false,
    config: {}
})


function startRecording(e) {
    record.value.config = e
    record.value.start = true;
    record.value.options = false
}

onMounted(() => {
    getRecordings()
})

</script>