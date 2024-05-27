<script setup>
import {ref, reactive, onMounted} from "vue"
import {db} from "../data/datos.js"

const productos = ref([])
onMounted (()=>{
  productos.value=db
}) 
</script>
<template>
    
    <div class="row p-0">
      <div v-for="productos in productos" class="col-lg-4 col-md-6 col-sm-12 my-3">
        <div class="card">
          <!-- <div class="card-header"></div> -->
          <div class="card-body">
            <h4 class="card-title">{{productos.nombre}}</h4>
            <p class="card-text">{{productos.descripcion}}</p>
          </div>
          <div class="card-footer">
            <div class="d-flex justify-content-between align-items-center">
              <div class="button btn btn-dark btn-sm text-white"><i class="bi bi-plus"></i></div>
              <div>S/. {{productos.precio}}</div>
            </div>
          </div>
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