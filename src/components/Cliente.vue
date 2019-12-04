<template>
    <div class="seccion">
        <div class="atributo">
            <span>{{ nombreCompleto}}</span>
        </div>
        <div class="atributo">
            <img :src="fotoPerfil" alt="" style="width:200px; height:200px">
        </div>
        <div class="atributo">
            <a :href="biografia" target="_blank">Biografia</a>
        </div>
        <div class="atributo">
            <span>Edad: {{ edad }}</span>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            nombres: 'Karim',
            apellidos: 'Lemaallam',
            fechaNacimiento: new Date(1998, 9, 23),
            fotoPerfil: 'https://pbs.twimg.com/profile_images/1084505553206943744/KAm2229K.jpg',
            biografia: 'https://twitter.com/karimlema9'
        }
    },
    computed: {
        nombreCompleto() {
            return `${this.nombres} ${this.apellidos}`
        },
        edad() {
            return this.calcularEdad(this.fechaNacimiento)
        }
    },
    methods: {
        calcularEdad(fecha) {
            let fechaActual = new Date()
            let diferencia = fechaActual - fecha
            return Math.floor(diferencia / (1000 * 60 * 60 * 24 * 365.25))
        }
    }
}
</script>

<style scoped>


</style>