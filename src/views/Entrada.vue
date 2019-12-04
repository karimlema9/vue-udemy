<template>
    <div>
        <anuncio/>
        <cliente/>
        <email/>
        <firma/>
        <boletos/>
    </div>
</template>

<script>
import Cliente from '@/components/Cliente.vue'
import Anuncio from '@/components/Anuncio.vue'
import Boletos from '@/components/Boletos.vue'
import Firma from '@/components/Firma.vue'
import Email from '@/components/Email.vue'


export default {
    components: {
        Cliente,
        Anuncio,
        Boletos,
        Firma,
        Email
    }
}
</script>

<style>

.seccion {
    font-size: 2.4rem;
    color: rgb(63, 63, 63);
    background-color: rgb(255, 255, 255);
    border-radius: 10px;
    margin: 10px;
    padding: 10px;
}

.atributo {
    margin: 10px;
}

</style>