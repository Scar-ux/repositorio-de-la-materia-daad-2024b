<script setup>
import {ref} from 'vue'; 
import planItem from './components/plan-item.vue';
const plans = ref(['El cafetero','El chelero','El intelectual']);
</script>


<template> 
   <div class="plans">
      <planItem v-for=" plan in plans" :key="plan" :name="plan"></planItem>
    </div>
</template>

<style scoped>

</style>