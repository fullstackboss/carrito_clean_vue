<script setup>
import Cabecera from "../components/Cabecera.vue"
import Productos from "../components/Productos.vue"
import Mycarrito from "../components/Mycarrito.vue"


import { onMounted } from "vue"
//importando la info del  carrito
import { db } from "../data/datos.js"
const listaProductos = ref([])
onMounted(() => {
    listaProductos.value = db
})


//configurando el carrito como objeto como PROPS
const carrito = ref([])


//funciones de agregar elimnar
import { ref } from 'vue';
const totalCarrito = ref(0)


//AGREGANDO Y RESTANDO
const agregaCarrito = (dato) => {
    const existeCarrito = carrito.value.findIndex(producto => producto.id === dato.id)
    console.log(existeCarrito);

    if (existeCarrito >= 0) {
        carrito.value[existeCarrito].cantidad++
        //console.log(carrito.value[existeCarrito].cantidad++)
    }
    else {
        dato.cantidad = 1
        carrito.value.push(dato)
    }
}
const restaCarrito = (dato) => {
    //console.log(dato);
}

</script>
<template>
    <div class="container-fluid px-0">
        <Cabecera />
    </div>
    <div class="container">
        <Mycarrito :vcarrito="carrito" :vtotalCarrito="totalCarrito" @vagregaCarrito="agregaCarrito"
            @vrestaCarrito="restaCarrito" />
        <Productos :vlistaProductos="listaProductos" @vagregaCarrito="agregaCarrito" @vrestaCarrito="restaCarrito" />
    </div>

</template>
<style lang="css" scoped></style>