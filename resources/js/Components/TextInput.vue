<script setup>
import { onMounted, ref } from "vue";

const model = defineModel({
    type: String,
    required: true,
});

// defineProps(['modelValue', 'placeholder']);

const input = ref(null);

onMounted(() => {
    if (input.value.hasAttribute("autofocus")) {
        input.value.focus();
    }
});

defineExpose({ focus: () => input.value.focus() });
</script>

<template>
    <input
        class="border-gray-300 focus:border-indigo-300 focus:ring-indigo-300 rounded-md shadow-sm p-4 text-lg font-semibold"
        v-model="model"
        ref="input"
    />
</template>
