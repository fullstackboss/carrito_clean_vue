<script setup>
const alerta=()=>{
    alert("Hello World")
}
</script>
<template>
    <div class="row border rounded mb-4">
        <div class="col-12 p-4">
            <div class="h5 pb-2">
                Resumen del carrito
            </div>
            <div class="d-flex justify-content-between p-2 align-items-center border rounded px-3">
                <div class="producto col-6">
                    Producto
                </div>
                <div class="cantidad">
                    Cantidad
                </div>
                <div class="cantidad">
                    Total
                </div>
                <div class="d-flex">
                    <div class="agregar pe-1">
                        <button @click="alerta" class="btn btn-dark btn-sm"><i class="bi bi-dash"></i></button>
                    </div>
                    <div class="restar">
                        <button class="btn btn-dark btn-sm"><i class="bi bi-plus"></i></button>
                    </div>
                    <div class="restar ps-3">
                        <button class="btn btn-dark btn-sm "><i class="bi bi-x-circle-fill"></i></button>
                    </div>
                </div>
            </div>
            <div class="h6 pt-3 d-flex justify-content-end">
                Total de la compra: s/. 00.00
            </div>
        </div>
    </div>
</template>



<style lang="css" scoped>
i{
  color:white;
  font-size: 22px;
}
.btn{
  padding: 2px;
  height: 30px;
  width: 30px;
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>