<template>
    <div class="seccion">
        <div class="atributo">
            <input v-model="email" @keyup.enter="actualitzarEmail" type="text">
        </div>
    </div>
</template>

<script>
export default {
    props: ['emailRecibido'],
    data() {
        return {
            email: ''
        }
    },
    methods: {
        actualitzarEmail() {
            this.$emit('onCambioEmail', this.email)
        }
    },
    watch: {
        emailRecibido() {
            this.email = this.emailRecibido
        }
    }
}
</script>

<style>

.email {
    text-align: left;
}

</style>