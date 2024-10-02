<script setup>
import { ref } from 'vue';
// Modelo
//item
const header = ref('App lista de compras');
const items = ref([
  {id:'0', label: '10 bolillos'},
  {id:'1', label: '1 pastel'},
  {id:'2', label: '1 kilo de jamon'},
  {id:'3', label: 'Nutella'},
  {id:'4', label: 'Pan tostado'}
]);
//item-model
const saveItem=()=> { 'saveItem' 
  items.value.push({id: items.value.length + 1, label: newItem.value});
  newItem.value=''; 
  //Clean de input 
}; 
//formulario
const newItem = ref("");
const newItemHighPriority = ref(false);
const editing =ref(true);
const activateEdition =(activate) => { 
  editing.value = activate; 
}; 

</script>

<template>
  <div class="header">
    <h1>
   <i 
   class="material-icons shopping-cart-icon">local_mall
  </i> 
    {{ header }} 
  </h1>
  <button v-if="editing" class="btn" @click="activateEdition(false)">Cancelar</button>
  <button v-else class="btn btn-primary" @click="activateEdition(true)">Agregar articulo </button>
  </div>
  <!--Agrupando entradas de usuario-->
  <form 
  class="add-item form"
  v-if="editing"
  v-on:submit.prevent="saveItem" >
  <!--Entrada de texto--> 
  <input v-model="newItem" type="text" placeholder="Agregar un articulo" />
  <!--Caja de seleccion de Prioridad-->
  <label>
    <input type="checkbox" v-model="newItemHighPriority" />
    Alta Prioridad 
  </label>
  <!--Boton-->
  <button class="btn btn-primary">
    Salvar Articulo
  </button>
  </form>
  <ul></ul>
  {{ iceCreamFlavors }}
  <ul></ul>
  {{ newItemHighPriority }}
  <!-- Lista -->
  <ul>
    <li v-for="item in items" :key="item.id"> 🎃 {{  item.label }} </li>
  </ul>
  <p v-if=" items.length === 0"> 🌸 NO HAY ELEMENTOS EN LA LISTA🌸</p>
</template>

<style scoped>
.shopping-cart-icon{
  font-size: 7rem;
}
</style>