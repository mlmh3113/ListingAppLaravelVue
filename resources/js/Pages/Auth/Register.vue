<script setup>
import Container from '../../Components/Container.vue';
import Title from '../../Components/Title.vue';
import TextLink from '../../Components/TextLink.vue';
import InputField from '../../Components/InputField.vue';
import PrimaryBtn from '../../Components/PrimaryBtn.vue';
import ErrorMessages from '../../Components/ErrorMessages.vue';
import { useForm } from '@inertiajs/vue3';

const form = useForm({
    name: '',
    email: '',
    password: '',
    password_confirmation: '',
});

const submit = () => {
    form.post(route('register'), {
        onFinish: () => form.reset('password', 'password_confirmation'),
    });
};

</script>

<template>

    <Container class="w-1/2">

        <div class="mb-8 text-center">
            <Title>Register</Title>
            <p>Already have an account? <TextLink routeName="home" label="Login"></TextLink></p>
        </div>

        <!-- Validation Errors -->

        <ErrorMessages :errors="form.errors"/>

        <form class="space-y-6">

            <InputField label="Name" type="text" placeholder="John Doe" icon="id-badge" v-model="form.name"/>
            <InputField label="Email" type="email" icon="at" v-model="form.email"/>
            <InputField label="Password" type="password" icon="key" v-model="form.password"/>
            <InputField label="Confirm Password" type="password" icon="key" v-model="form.password_confirmation"/>

            <p class="text-sm text-slate-500 dark:text-slate-400">
                By creating an account, you agree to out Terms of Service and Privacy Policy.
            </p>

            <PrimaryBtn @click="submit" :disabled="form.processing">Register</PrimaryBtn>

        </form>

    </Container>

</template>

<style scoped>

</style>
