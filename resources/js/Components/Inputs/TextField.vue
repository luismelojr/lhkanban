<script setup>
import { onMounted, ref } from 'vue';

defineProps({
    modelValue: {
        type: String,
        required: true,
    },
    placeholder: {
        type: String,
        default: '',
    },
});

defineEmits(['update:modelValue']);

const input = ref(null);

onMounted(() => {
    if (input.value.hasAttribute('autofocus')) {
        input.value.focus();
    }
});

defineExpose({ focus: () => input.value.focus() });
</script>

<template>
    <input
        class="border-[1px] mt-[0.5rem] py-[1rem] px-[0.75rem] focus:border-primary focus:ring-primary rounded-[0.25rem] placeholder-[#94A3B8] text-[0.875rem] text-gray-800"
        :class="{'border-red-500': $attrs.errors, 'border-gray-200': !$attrs.errors}"
        :value="modelValue"
        @input="$emit('update:modelValue', $event.target.value)"
        :placeholder="placeholder"
        ref="input"
    />
</template>
