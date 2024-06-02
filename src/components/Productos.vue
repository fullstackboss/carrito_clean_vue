<script setup>
import {ref, onMounted} from "vue"
import {db} from "../data/datos.js"

const listaproductos = ref([])
onMounted (()=>{
  listaproductos.value=db
}) 
</script>
<template>
    
    <div class="row p-0">
      <div v-for="elements in listaproductos" class="col-lg-4 col-md-6 col-sm-12 my-3">
        <div class="card">
          <!-- <div class="card-header"></div> -->
          <div class="card-body">
            <div class="d-flex justify-content-between align-items-center mb-3">
              <h4 class="card-title">{{elements.nombre}}</h4>
              <img :src="'/img/' + elements.imagen" alt="" width="50">
            </div>
            <p class="card-text">{{elements.descripcion}}</p>
          </div>
          <div class="card-footer">
            <div class="d-flex justify-content-between align-items-center">
              <div class="button btn btn-dark btn-sm text-white"><i class="bi bi-plus"></i></div>
              <div>S/. {{elements.precio}}</div>
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
img{
  width: 60px;
  border-radius: 50%;
  border: 1px solid #f7f2eb;
  background-color: #f3f0eb;
}
</style>