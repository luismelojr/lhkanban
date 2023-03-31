<script setup>
import ApplicationLogo from '@/Components/ApplicationLogo.vue';
import { Link } from '@inertiajs/vue3';
import Logo from "@/Components/Icons/Logo.vue";
</script>

<template>
    <div class="min-h-screen min-w-full grid grid-cols-2 bg-gray-100">
        <div class="py-[2.5rem] px-[7rem]">
            <Link href="/">
                <Logo />
            </Link>
            <div class="mt-[8rem]">
                <slot />
            </div>
        </div>
        <div class="h-full bg-hero-bg bg-cover bg-no-repeat bg-center">
        </div>
    </div>
</template>
