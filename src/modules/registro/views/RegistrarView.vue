<template>
    <div>
        <h2>Formulario de registro</h2>
        <Form :validation-schema="schema" @submit="onSubmit">
            <div class="form">
                <label for="nombre">Nombre:</label>
                <Field id="nombre" v-model="nombre" name="nombre" type="text" placeholder="ingrese su nombre"></Field>
                <ErrorMessage name="nombre"></ErrorMessage>
            </div>
            <div class="form">
                <label for="corrreo">Correo:</label>
                <Field id="correo" v-model="email" name="email" type="email" placeholder="ingrese su email"></Field>
                <ErrorMessage name="email"></ErrorMessage>
            </div>
            <div class="form">
                <button type="submit">Registrar</button>
            </div>
        </Form>
    </div>
</template>
<script setup>
import {Form, Field, ErrorMessage} from 'vee-validate';
import { schema } from '../schemas/validationSchema';
import { useRegistrarStore } from '../stores/registrarStore';
import {ref} from 'vue';

const registrarStore = useRegistrarStore();

const nombre = ref('');
const email = ref ('');

const onSubmit = () => {
    registrarStore.guardarRegistro(nombre.value, email.value)
    console.log("se ha enviado el formulario")
}
</script>
<style scoped>

.form{
    margin-bottom: 10px;
}

</style>