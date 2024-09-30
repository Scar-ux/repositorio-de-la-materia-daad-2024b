<script setup>
import { ref } from 'vue';
// Modelo
const header = ref('App lista de compras');
const items = ref([
  {id:'0', label: '10 bolillos'},
  {id:'1', label: '1 pastel'},
  {id:'2', label: '1 kilo de jamon'},
  {id:'3', label: 'Nutella'},
  {id:'4', label: 'Pan tostado'}
]);
const newItem = ref("");
const newItemHighPriority = ref(false);
</script>

<template>
  <h1>
   <i class="material-icons shopping-cart-icon">local_mall</i> 
    {{ header }} 
  </h1>
  <form v-on:submit.prevent="items.push({id: items.length + 1, label: newItem})" class="add-item form">
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
</template>

<style scoped>
.shopping-cart-icon{
  font-size: 7rem;
}
</style>