<script setup>
import Precio from "../components/Precio.vue"
const props = defineProps({
  vlistaProductos: {
    type: Object,
    required: true,
  }
})
defineEmits(['vagregaCarrito'])


</script>
<template>
  <div class="row p-0">
    <div v-for="producto in vlistaProductos" class="col-lg-4 col-md-6 col-sm-12 my-3">
      <div class="card">
        <!-- <div class="card-header"></div> -->
        <div class="card-body">
          <div class="d-flex justify-content-between align-items-center mb-3">
            <h4 class="card-title">{{ producto.nombre }}</h4>
            <img :src="'/img/' + producto.imagen" alt="" width="50">
          </div>
          <p class="card-text">{{ producto.descripcion }}</p>
        </div>
        <div class="card-footer bg-white">
          <div class="d-flex justify-content-between align-items-center">
            <div class="d-flex">
              <div @click="$emit('vagregaCarrito', producto)" class="button btn btn-dark btn-sm text-white me-1"><i
                  class="bi bi-plus"></i>
              </div>
              <!--               <div @click="$emit('vincrementaCantidad', producto)" class="button btn btn-dark btn-sm text-white"><i
                  class="bi bi-dash"></i>
              </div> -->
            </div>
            <Precio :vprecio="producto.precio" />
          </div>
        </div>
      </div>
    </div>
  </div>

</template>
<style lang="css" scoped>
i {
  color: white;
  font-size: 22px;
}

.btn {
  padding: 2px;
  height: 30px;
  width: 30px;
  display: flex;
  justify-content: center;
  align-items: center;
}

img {
  width: 60px;
  border-radius: 50%;
  border: 1px solid #f7f2eb;
  background-color: #f3f0eb;
}
</style>