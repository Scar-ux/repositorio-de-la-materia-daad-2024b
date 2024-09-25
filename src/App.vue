
<script setup>
import { ref} from 'vue';
//model
const header = ref('App lista de compras');
const items = ref ([ 
    {id:'0',label: 'Nuguettes'},
   { id:'1',label: '10 bolillos'},
    {id:'2',label: 'jamon de pierna'},
   { id:'3',label: 'Nutella'},
    {id:'4',label: 'Pollo'},
    {id:'5',label: 'Huevo'}
]);
const newItem=ref("");
</script>

<template>
<h1>
    <i class="material-icons shopping-cart-icon">local_mall</i>
    {{ header }}
    </h1>
    <input v-model.lazy= "newItem" type="type" placeholder="Agregar articulo"> {{ newItem }}</input>
    <ul>
        <li v-for="item in items ":key="item.id"> 🎃{{ item.label }}</li>
    </ul>
</template>

<style scoped>
.shopping-cart-icon{
    font-size: 5rem;
}
</style>
