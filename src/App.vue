<script setup>
import { ref,computed } from 'vue';  
// Modelo
//item
const header = ref('App lista de compras');
const items = ref([
  {id:'0', label: '10 bolillos', purchased: false, Priority: true},
  {id:'1', label: '1 pastel',purchased: false,Priority: true},
  {id:'2', label: '1 kilo de jamon', purchased: true, Priority: true},
  {id:'3', label: 'Nutella', purchased: true, Priority: false},
  {id:'4', label: 'Pan tostado',purchased: false, Priority: true}
]);
//item-model
const saveItem=()=> { 'saveItem' 
  items.value.push({id: items.value.length + 1, label: newItem.value});
  newItem.value=''; 

   // Reiniciendo la entrada de texto
   newItem.value = "";
  newItemHighPriority.value = false;
};
// Funcion que alterna el valor de la variable editing
const doEdit = (edit) => {
  editing.value = edit;
  // Limpiando la entrada de texto
  // en caso de que se oculte o muestre
  // el formulario
  newItem.value = "";
  newItemHighPriority.value = false;
};
  //Clean de input 

//formulario
const newItem = ref("");
const newItemHighPriority = ref(false);
const editing =ref(true);
const activateEdition =(activate) => { 
  editing.value = activate; 

}; 
//Alternando estado de compra del item
const togglePurchased =(item)=>{
  item.purchased =!item.purchased; 
}; 



//creando una propiedad computada 
const characterCount = computed(()=>{
  // Toda propiedad computada debe regresar un valor
  return newItem.value.length;
});

// Creando propiedad computada que invierte items de la lista
const reversedItems = computed(() => {
  return [...items.value].reverse(); 
});

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
  <!--Colocando un hyperlink-
  <a v-bind:href="'https://' + (newItem =='' ? 'www.google.com' : newItem)  " target="_blank"> {{ newItem =="" ? "🌑Link" : newItem }}</a>-->

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
  <button 
  :disabled="newItem.length===0" 
  class="btn btn-primary">
    Salvar Articulo
  </button>

<!--Contador-->
<p class="counter">
    {{ characterCount }} /200
    </p>

  </form>
  <ul></ul>
  {{ iceCreamFlavors }}
  <ul></ul>
  {{ newItemHighPriority }}

  
  <!-- Lista objetos-->
  <ul>
    ...
<li 
	v-for="({ id, label, purchased, highPriority }, index) in reversedItems"
  :class="{ strikeout: purchased, priority: highPriority }" 
	@click="togglePurchased(reversedItems[index])" 
  v-bind:key="id">
	  🔹 {{ label }}
</li>

    </ul>

  <p v-if=" items.length === 0"> 🌸 NO HAY ELEMENTOS EN LA LISTA🌸</p>



</template>

<style scoped>
.shopping-cart-icon{
  font-size: 7rem;
}
</style>