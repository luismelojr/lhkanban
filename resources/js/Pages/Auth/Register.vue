<script setup>
import GuestLayout from '@/Layouts/GuestLayout.vue';
import InputError from '@/Components/InputError.vue';
import { Head, useForm } from '@inertiajs/vue3';
import NavLink from '@/Components/Navigation/NavLink.vue';
import LoadButton from '@/Components/Inputs/LoadButton.vue';
import TextField from '@/Components/Inputs/TextField.vue';
import TextFieldPassword from '@/Components/Inputs/TextFieldPassword.vue';
import TextLabel from '@/Components/Inputs/TextLabel.vue';

const form = useForm({
    name: '',
    email: '',
    password: '',
    password_confirmation: '',
    terms: false,
});

const submit = () => {
    form.post(route('register'), {
        onFinish: () => form.reset('password', 'password_confirmation'),
    });
};
</script>

<template>
    <GuestLayout>
        <Head title="Register" />

        <div>
            <h1 class="font-titillium text-4xl font-bold">Registre-se já</h1>
            <p class="mt-[1rem] text-[1rem] text-gray-600 font-titillium">Registre-se agora e tenha acesso exclusivo aos nossos serviços.</p>
        </div>
        <form class="mt-[2.5rem]" @submit.prevent="submit">
            <div>
                <TextLabel value="Nome" />
                <TextField type="text" v-model="form.name" class="w-full" placeholder="Digite seu nome" :errors="form.errors.name"/>
                <InputError :message="form.errors.name" class="mt-2" />
            </div>
            <div class="mt-[1rem]">
                <TextLabel value="E-mail" />
                <TextField type="email" v-model="form.email" class="w-full" placeholder="Digite seu e-mail" :errors="form.errors.email"/>
                <InputError :message="form.errors.email" class="mt-2" />
            </div>
            <div class="mt-[1rem]">
                <TextLabel value="Senha" />
                <TextFieldPassword v-model="form.password" class="w-full" placeholder="Digite sua senha" :errors="form.errors.password"/>
                <InputError :message="form.errors.password" class="mt-2" />
            </div>
            <div class="mt-[1rem]">
                <TextLabel value="Confirmar senha" />
                <TextFieldPassword v-model="form.password_confirmation" class="w-full" placeholder="Confirme sua senha" :errors="form.errors.password_confirmation"/>
                <InputError :message="form.errors.password_confirmation" class="mt-2" />
            </div>
            <LoadButton type="submit" class="mt-[2rem] w-full" :loading="form.processing">Cadastrar</LoadButton>
        </form>
        <div class="mt-8">
            <p class="text-gray-600 text-[0.875rem]">Já possui conta? <NavLink :href="route('login')">Login</NavLink></p>
        </div>
    </GuestLayout>
</template>
