<script setup>
//Computed property
import { computed } from 'vue';

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
const totalPagar = computed(() => {
    return props.vcarrito.reduce((total, producto) => total + (producto.cantidad * producto.precio), 0)
})


defineEmits(['vagregaCarrito', 'vincrementaCantidad', 'vdecrementaCantidad', 'veliminarProducto', 'vlimpiarCarrito'])
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
                            <img class="img-fluid" :src="'/img/' + producto.imagen" alt="" width="40">
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
                                <button @click="$emit('vdecrementaCantidad', producto.id)"
                                    class="btn btn-light btn-sm"><i class="bi bi-dash"></i></button>
                                <button @click="$emit('vincrementaCantidad', producto.id)"
                                    class="btn btn-light btn-sm me-0"><i class="bi bi-plus"></i></button>
                                <button @click="$emit('veliminarProducto', producto.id)"
                                    class="btn btn-light btn-sm "><i class="bi bi-trash"></i></button>
                            </div>
                        </div>
                    </div>
                </div>
                <!-- Fin Items -->
                <div class="pt-2 d-flex justify-content-between">
                    <div class="">
                        <button @click="$emit('vlimpiarCarrito')" class="btn btn-danger w-100 px-3">
                            <i class="bi bi-trash pe-2 vc"></i> Limpiar</button>
                    </div>
                    <div class="d-flex justify-content-center align-items-center">
                        <div>Total de la compra: </div>
                        <div class="bg-dark text-white px-2 py-1 rounded ms-2 fs-6">s/. {{
                            totalPagar
                            }}</div>
                    </div>
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

i.vc {
    color: #ffffff;
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