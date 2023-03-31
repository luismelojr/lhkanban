<script setup>
import GuestLayout from '@/Layouts/GuestLayout.vue';
import InputError from '@/Components/InputError.vue';
import {Head, useForm} from '@inertiajs/vue3';
import TextLabel from "@/Components/Inputs/TextLabel.vue";
import TextField from "@/Components/Inputs/TextField.vue";
import NavLink from "@/Components/Navigation/NavLink.vue";
import TextFieldPassword from "@/Components/Inputs/TextFieldPassword.vue";
import LoadButton from "@/Components/Inputs/LoadButton.vue";

defineProps({
    canResetPassword: {
        type: Boolean,
    },
    status: {
        type: String,
    },
});

const form = useForm({
    email: '',
    password: '',
    remember: false,
});

const submit = () => {
    form.post(route('login'), {
        onFinish: () => form.reset('password'),
    });
};
</script>

<template>
    <GuestLayout>
        <Head title="Log in" />

        <div>
            <h1 class="font-titillium text-4xl font-bold">Acesse a plataforma</h1>
            <p class="mt-[1rem] text-[1rem] text-gray-600 font-titillium">Faça login ou registre-se para começar a construir seus projetos ainda hoje.</p>
        </div>
        <form class="mt-[2.5rem]" @submit.prevent="submit">
            <div>
                <TextLabel value="E-mail" />
                <TextField type="email" v-model="form.email" class="w-full" placeholder="Digite seu e-mail" :errors="form.errors.email"/>
                <InputError :message="form.errors.email" class="mt-2" />
            </div>
            <div class="mt-[1rem]">
                <div class="flex items-center justify-between">
                    <TextLabel value="Senha" />
                    <NavLink href="/">Esqueceu a senha?</NavLink>
                </div>
                <TextFieldPassword v-model="form.password" class="w-full" placeholder="Digite sua senha" :errors="form.errors.password"/>
                <InputError :message="form.errors.password" class="mt-2" />
            </div>
            <LoadButton type="submit" class="mt-[2rem] w-full" :loading="form.processing">Entrar</LoadButton>
        </form>
        <div class="mt-8">
            <p class="text-gray-600 text-[0.875rem]">Ainda não tem uma conta? <NavLink :href="route('register')">Inscreva-se</NavLink></p>
        </div>
    </GuestLayout>
</template>
