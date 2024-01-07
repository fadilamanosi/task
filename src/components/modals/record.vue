<template>
    <div class="record-modal">
        <div class="container">
            <div class="header">
                <span>New recording</span>
                <Close class="close" @click="$emit('close')"></Close>
            </div>
            <div class="body">
                <div>
                    <p>Save the recording in</p>
                    <input id="save-to" type="file" hidden>
                    <label for="save-to" class="save-to">
                        <span>
                            Select a project
                        </span>
                        <ArrowDown></ArrowDown>
                    </label>
                </div>

                <div class="options">
                    <div>
                        <span>Record screen</span>
                        <Toggle @value="form.screen = $event" :checked="form.screen"></Toggle>
                    </div>
                    <div>
                        <span>Record camera</span>
                        <Toggle @value="form.camera = $event" :checked="form.camera"></Toggle>
                    </div>
                    <div>
                        <span>Record mic</span>
                        <Toggle @value="form.mic = $event" :checked="form.mic"></Toggle>
                    </div>
                </div>

                <div class="button">
                    <Button :disabled="(!form.mic && !form.camera && !form.screen) ? true : false" :class="'large'"
                        @click="record()" :background="'#0CABD8'" :text="'white'">
                        Start recording
                    </Button>
                </div>
            </div>
        </div>
    </div>
</template>


<script setup>

import Toggle from "@/components/reusables/toggle.vue"
import Button from "@/components/reusables/button.vue"
import Close from "../icons/close.vue";
import { ref } from "vue";
import ArrowDown from "../icons/arrow-down.vue";

const form = ref({
    screen: true,
    camera: true,
    mic: false
})

const emits = defineEmits(['close', 'record']);

function record() {
    if (!(!form.value.mic && !form.value.camera && !form.value.screen)) {
        emits('record', form.value)
    }
}


</script>

