<template>
    <div class="anuncio">
        <span v-once>{{presentaciones[indice] }}</span>
    </div>
</template>

<script>
export default {
    data() {
        return {
            presentaciones: [
                'karim - 15:30',
                'Joker - 17:00',
                'Avengers - 18:30',
                'El Rey Leon - 22:00'
            ],
            indice: 0
        }
    },
    methods: {
        mostrarAnuncio() {
            this.indice++

            if(this.indice == this.presentaciones.length) {
                this.indice  = 0
                this.$destroy()
            }
        }
    },
    beforeCreate() {
            console.log('beforeCreate')        
    },
    created() {
        console.log('created')
    },
    beforeMount() {
        console.log('beforeMount')
    },
    mounted() {
        console.log('mounted')
        setInterval(this.mostrarAnuncio, 2000)
        this.mostrarAnuncio()
    },
    beforeUpdated() {
        console.log('beforeUpdated')
    },
    updated() {
        console.log('updated')
    },
    beforeDestroy() {
        console.log('beforeDestroy')
    },
    destroyed() {
        console.log('destroyed')
    }
}
</script>

<style>
.anuncio {
    margin: 10px;
    font-size: 2rem;

    border-top-color: white;
    border-top-width: 1px;
    border-top-style: solid;

    border-bottom-color: white;
    border-bottom-width: 1px;
    border-bottom-style: solid;

}
</style>