<script setup>
defineProps({
    type: {
        type: String,
        default: 'button',
    },
    loading: {
        type: Boolean,
        default: false,
    },
})
</script>

<template>
    <button class="py-[1rem] px-[1.5rem] flex justify-center items-center bg-primary rounded-[0.625rem] text-white text-[1rem] font-bold hover:bg-[#9F67FF] transition-all disabled:opacity-50 disabled:cursor-not-allowed" v-bind="$attrs" :disabled="loading">
        <slot v-if="!loading" />
        <span v-else>
            <svg xmlns="http://www.w3.org/2000/svg" fill="none" viewBox="0 0 24 24" stroke-width="1.5" stroke="currentColor" class="w-5 h-5 animate-spin">
              <path stroke-linecap="round" stroke-linejoin="round" d="M16.023 9.348h4.992v-.001M2.985 19.644v-4.992m0 0h4.992m-4.993 0l3.181 3.183a8.25 8.25 0 0013.803-3.7M4.031 9.865a8.25 8.25 0 0113.803-3.7l3.181 3.182m0-4.991v4.99" />
            </svg>
        </span>
    </button>
</template>
