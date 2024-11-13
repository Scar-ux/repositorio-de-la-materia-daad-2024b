<template>
  <div @click="selectPlan" class="plan">
    <div class="description">
      <span class="title">
        {{ name }} {{ selected ? '🌟' : '' }}
      </span>
    </div>
  </div>
</template>

<script setup>
//import ref function
import { ref } from 'vue';

//Usando un macro para
//definir las props
//defineProps(['name', 'planIcon']);
const props = defineProps({
  name: {
    type: String,
    required: true
  }
});
//Define event
const emit = defineEmits(['select']);
//Variable que permite recordar
//si el plan a sido seleccionado 
const selected = ref(false);
//Funcion que permite cambiar el estado de la variable
//selected
const selectPlan = () => {
selected.value = true;
//Emitir el evento de que el 
//plan ha sido seleccionado
emit('select', props.name);
};
</script>

<style scoped>

</style>
  