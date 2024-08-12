<template>
    <div>
      <h4>Choisissez une opération :</h4>
      <div class="form-check" v-for="(op, index) in operations" :key="index">
        <input
          class="form-check-input"
          type="radio"
          :id="op"
          :value="op"
          v-model="selectedOperation"
        />
        <label class="form-check-label" :for="op">{{ op }}</label>
      </div>
    </div>
  </template>
  
  <script setup>
  import { ref, watch } from 'vue';
  
  // Définir les props en utilisant `defineProps`
  const props = defineProps({
    onSelect: Function,
  });
  
  const operations = ['Addition', 'Multiplication', 'Division', 'Soustraction'];
  const selectedOperation = ref(operations[0]);
  
  // Observer les changements de l'opération sélectionnée et appeler la fonction onSelect
  watch(selectedOperation, (newOp) => {
    props.onSelect(newOp);
  });
  </script>
  