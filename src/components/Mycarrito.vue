<script setup>
const props = defineProps({
    vtotalCarrito: {
        type: String,
        required: true,
    },
    vcarrito: {
        type: Array,
        required: true,
    }
})

defineEmits(['vagregaCarrito,vrestaCarrito'])
</script>
<template>
    <div class="row border rounded mb-4">
        <div class="col-12 p-4">
            <div class="h5 pb-2">
                Resumen del carrito
            </div>
            <div v-if="vcarrito.length === 0"
                class="d-flex justify-content-center p-2 align-items-center border rounded px-3">
                El carrito esta vacio
            </div>
            <!-- Cuerpo Items -->
            <div v-else id="carrito">
                <!-- Items -->
                <div v-for="producto in vcarrito">
                    <div class="d-flex justify-content-between p-2 align-items-center border rounded px-3 mb-1">
                        <div class="producto col-1">
                            <img class="img-fluid" :src="'/img/' + producto.imagen" alt="">
                        </div>
                        <div class="producto col-5">
                            {{ producto.nombre }}
                        </div>
                        <div class="cantidad">
                            {{ producto.cantidad }}
                        </div>
                        <div class="cantidad">
                            {{ producto.precio }}
                        </div>
                        <div class="d-flex">
                            <div class="restar btn-group">
                                <button @click="$emit('vagregaCarrito')" class="btn btn-light btn-sm me-0"><i
                                        class="bi bi-plus"></i></button>
                                <button @click="$emit('vrestaCarrito')" class="btn btn-light btn-sm"><i
                                        class="bi bi-dash"></i></button>
                                <button class="btn btn-light btn-sm "><i class="bi bi-trash"></i></button>
                            </div>
                        </div>
                    </div>
                </div>
                <!-- Fin Items -->
                <div class="h6 pt-3 d-flex justify-content-end">
                    Total de la compra: s/. {{ vtotalCarrito }}
                </div>
            </div>

        </div>
    </div>
</template>



<style lang="css" scoped>
i {
    color: #222;
    font-size: 20px;
}

.btn {
    padding: 2px;
    height: 30px;
    width: 30px;
    display: flex;
    justify-content: center;
    align-items: center;
}
</style>