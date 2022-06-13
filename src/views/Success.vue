<template>
    <div class="page-success">
        <div class="column is-multiline">
            <div class="column is-12">
                <h1 class="title">Greacias por su compra</h1>

                <p>Su orden sera procesada en las proximas 24 horas</p>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'Success',
    mounted() {
        document.title = 'Exito | TCGStore'
    },
}
</script>