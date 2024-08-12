<template>
    <div>
      <div v-if="error" class="alert alert-danger">{{ error }}</div>
      <div v-else class="alert alert-primary">Résultat : {{ result }}</div>
    </div>
  </template>
  
  <script setup>
  import { defineProps } from 'vue';
  
  // Définir les props
  const props = defineProps({
    result: {
      type: Number,
      required: true
    },
    error: {
      type: String,
      default: ''
    }
  });
  </script>
  