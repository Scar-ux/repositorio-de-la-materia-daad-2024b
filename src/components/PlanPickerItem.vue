<template>
  <div @click="selectPlan" class="plan">
    <div class="description">
      <span class="title">
        {{ name }} {{ isSelected ? '🌟' : '' }}
      </span>
    </div>
  </div>
</template>

<script setup>
//
import {computed} from 'vue'; 

//Usando un macro para
//definir las props
//defineProps(['name', 'planIcon']);
const props = defineProps({
  name: {
    type: String,
    required: true
  },
  selectPlan: String
});
//Define event
const emit = defineEmits(['select']);
//Funcion que permite cambiar el estado de la variable
//selected
const selectPlan = () => {
//Emitir el evento de que el 
//plan ha sido seleccionado
emit('select', props.name); 
};
//crteando una propiedad computada
//para saber si el plan ha sido seleccionado
const isSelected = computed(()=>{
  return props.name === props.selectedPlan;
}); 
</script>

<style scoped>

</style>
  