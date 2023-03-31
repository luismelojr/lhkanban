<script setup>
import {computed, onMounted, ref} from 'vue';

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
const isPasswordVisible = ref(true);

onMounted(() => {
    if (input.value.hasAttribute('autofocus')) {
        input.value.focus();
    }
});

defineExpose({ focus: () => input.value.focus() });

const togglePasswordVisibility = () => {
    const type = input.value.getAttribute('type') === 'password' ? 'text' : 'password';
    isPasswordVisible.value = !isPasswordVisible.value;
    input.value.setAttribute('type', type);
    input.value.focus();
};


</script>

<template>
    <div class="relative flex items-center mt-[0.5rem]">
        <input
            class="rounded-[0.25rem] flex-1 h-full px-[0.75rem] py-[1rem] focus:border-primary focus:ring-primary placeholder-[#94A3B8] text-[0.875rem] text-gray-800 pr-12"
            :class="{'border-red-500': $attrs.errors, 'border-gray-200': !$attrs.errors}"
            type="password"
            :value="modelValue"
            @input="$emit('update:modelValue', $event.target.value)"
            :placeholder="placeholder"
            ref="input"
        >
        <button type="button" @click.prevent="togglePasswordVisibility" class="absolute right-[0.75rem]">
            <svg v-if="isPasswordVisible" xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-6 h-6 text-[#94A3B8]">
                <path stroke-linecap="round" stroke-linejoin="round" d="M3.98 8.223A10.477 10.477 0 001.934 12C3.226 16.338 7.244 19.5 12 19.5c.993 0 1.953-.138 2.863-.395M6.228 6.228A10.45 10.45 0 0112 4.5c4.756 0 8.773 3.162 10.065 7.498a10.523 10.523 0 01-4.293 5.774M6.228 6.228L3 3m3.228 3.228l3.65 3.65m7.894 7.894L21 21m-3.228-3.228l-3.65-3.65m0 0a3 3 0 10-4.243-4.243m4.242 4.242L9.88 9.88" />
            </svg>

            <svg v-else xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-6 h-6 text-[#94A3B8]">
                <path stroke-linecap="round" stroke-linejoin="round" d="M2.036 12.322a1.012 1.012 0 010-.639C3.423 7.51 7.36 4.5 12 4.5c4.638 0 8.573 3.007 9.963 7.178.07.207.07.431 0 .639C20.577 16.49 16.64 19.5 12 19.5c-4.638 0-8.573-3.007-9.963-7.178z" />
                <path stroke-linecap="round" stroke-linejoin="round" d="M15 12a3 3 0 11-6 0 3 3 0 016 0z" />
            </svg>
        </button>
    </div>
</template>

<!--class="border-gray-200 mt-[0.5rem] py-[1rem] px-[0.75rem] focus:border-primary focus:ring-primary rounded-[0.25rem] placeholder-[#94A3B8] text-[0.875rem] text-gray-800"-->
