<template>
    <div class="seccion">
        <div class="atributo">
            <input @keyup.enter="actualitzarEmail" type="text">
        </div>
        <div class="aributo email">
            <span>
                Email: {{ email }}
            </span>
        </div>
    </div>
</template>

<script>
export default {
    data() {
        return {
            email: ''
        }
    },
    methods: {
        actualitzarEmail(event) {
            this.email = event.target.value
        }
    }
}
</script>

<style>

.email {
    text-align: left;
}

</style>