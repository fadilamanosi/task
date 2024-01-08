<template>
    <div class="recording">
        <div>
            <span class="text">Live preview</span>
            <video ref="video" autoplay muted playsinline class="camera"></video>

            <div class="button">
                <Button @click="start()" :background="'#0CABD8'" :text="'white'">Start Recording</Button>
            </div>
        </div>

    </div>
</template>

<script setup>
import Button from "@/components/reusables/button.vue"
import { onMounted, ref } from "vue";


const props = defineProps(['config']);
const video = ref('');

let stream;

const startRecording = async () => {

    try {

        stream = await navigator.mediaDevices.getUserMedia({
            audio: props.config.mic,
            video: { facingMode: 'environment', width: 1280 },
        })
        video.value.srcObject = stream

    } catch (error) {
        console.error(error)
    }
}

onMounted(() => {
    if ('mediaDevices' in navigator && 'getUserMedia' in navigator.mediaDevices) {
        startRecording()
    }
})
</script>