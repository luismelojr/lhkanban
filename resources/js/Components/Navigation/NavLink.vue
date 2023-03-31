<script setup>
import { Link } from '@inertiajs/vue3';

const props = defineProps({
    href: {
        type: String,
        required: true,
    },
})
</script>

<template>
    <Link :href="props.href" class="text-primary text-[0.875rem] font-titillium font-bold hover:underline">
        <slot />
    </Link>
</template>
