<template>
    <div class="create-car-form">
        <input type="text"  placeholder="Matricula" v-model="matricula"/>
        <input type="text"  placeholder="Marca" v-model="marca"/>
        <input type="button" value="Save" @click="handleClickSave" />
        <div v-if="isError" class="create-car-form-error">
            Error
        </div>
    </div>
</template>

<script>
import { ref } from '@vue/reactivity';
    export default {
        props: {},
        emits: ['submit'],
        setup(props, {emit}) {
            const matricula = ref(null)
            const marca = ref(null)
            const isError = ref(false)
            const handleClickSave = () => {
                if(!!matricula.value && !!marca.value) {
                    isError.value = false;
                    emit('submit', {
                        matricula: matricula.value,
                        marca: marca.value
                    })
                    matricula.value = null,
                    marca.value = null
                } else {
                    isError.value = true;
                }

            }
            return {
                ...props,
                matricula,
                marca,
                isError,
                handleClickSave
            }
        }
    }
    
</script>

<style>
.create-car-form {
    padding: 20px;
    border: 1px solid #dddddd;
    border-radius: 8px;
    display:flex;
    flex-direction: column;
    gap: 10px;
    max-width: 50vw;   
}
.create-car-form-error {
    color: red;
}
</style>