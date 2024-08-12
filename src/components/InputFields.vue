<template>
    <div>
      <div class="mb-3">
        <label for="value1" class="form-label">Valeur 1</label>
        <input v-model.number="value1" type="number" class="form-control" id="value1" />
      </div>
      <div class="mb-3">
        <label for="value2" class="form-label">Valeur 2</label>
        <input v-model.number="value2" type="number" class="form-control" id="value2" />
      </div>
    </div>
  </template>
  
  <script setup>
  import { ref, watch } from 'vue';
  
  // Définir les props
  const props = defineProps({
    onInput: Function,
  });
  
  const value1 = ref(0);
  const value2 = ref(0);
  
  // Observer les changements dans les valeurs et appeler la fonction onInput
  watch([value1, value2], () => {
    props.onInput({ value1: value1.value, value2: value2.value });
  });
  </script>
  