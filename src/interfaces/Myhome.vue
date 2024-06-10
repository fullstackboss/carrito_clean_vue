<script setup>
import Cabecera from "../components/Cabecera.vue"
import Productos from "../components/Productos.vue"
import Mycarrito from "../components/Mycarrito.vue"

/* escucha todo */
import { watch } from "vue"
import { onMounted } from "vue"
//importando la info del  carrito
import { db } from "../data/datos.js"
const listaProductos = ref([])
onMounted(() => {
    listaProductos.value = db

    const carritoStorage = localStorage.getItem('carrito')
    if (carritoStorage) {
        carrito.value = JSON.parse(carritoStorage)
    }
})


//configurando el carrito como objeto como PROPS
const carrito = ref([])


//funciones de agregar elimnar
import { ref } from 'vue';
const totalCarrito = ref(0)


//AGREGANDO AL CARRITO
const agregaCarrito = (dato) => {
    const existeCarrito = carrito.value.findIndex(producto => producto.id === dato.id)

    if (existeCarrito >= 0) {
        carrito.value[existeCarrito].cantidad++
    }
    else {
        dato.cantidad = 1
        carrito.value.push(dato)
    }
}
/* Sumando y restando */

const incrementaCantidad = (id) => {
    const index = carrito.value.findIndex(producto => producto.id === id)
    if (carrito.value[index].cantidad >= 5) return
    carrito.value[index].cantidad++
}
const decrementaCantidad = (id) => {
    const index = carrito.value.findIndex(producto => producto.id === id)
    if (carrito.value[index].cantidad <= 1) return
    carrito.value[index].cantidad--
}

/* Eliminando producto */
const eliminarProducto = (id) => {
    carrito.value = carrito.value.filter(producto => producto.id !== id)
}
/* Vaciando el carrito */
const limpiarCarrito = () => {
    carrito.value = []
}

const guardarLocalStorage = () => {
    localStorage.setItem('carrito', JSON.stringify(carrito.value))
}

//escucha todo
watch(carrito, () => {
    guardarLocalStorage()
}, {
    deep: true
})

</script>
<template>
    <div class="container-fluid px-0">
        <Cabecera />
    </div>
    <div class="container">
        <Mycarrito :vcarrito="carrito" :vtotalCarrito="totalCarrito" @vagregaCarrito="agregaCarrito"
            @vincrementaCantidad="incrementaCantidad" @vdecrementaCantidad="decrementaCantidad"
            @veliminarProducto="eliminarProducto" @vlimpiarCarrito="limpiarCarrito" />
        <Productos :vlistaProductos="listaProductos" @vagregaCarrito="agregaCarrito" />
    </div>

</template>
<style lang="css" scoped></style>