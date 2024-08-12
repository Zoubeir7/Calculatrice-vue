<template>
    <div class="container mt-5">
      <h1 class="text-center">Calculatrice</h1>
  
      <!-- Sélection de l'opération -->
    <div class="mt-4">
        <h4>Choisissez une opération :</h4>
        <div class="form-check" v-for="(op, index) in operations" :key="index">
            
            <label class="form-check-label" :for="op">{{ op }}</label>

            <input class="form-check-input" type="radio" :id="op" :value="op" v-model="selectedOperation"/>
        </div>
    </div>
  
      <!-- Champs de saisie pour les valeurs (affichés uniquement après sélection d'une opération) -->
      <div v-if="selectedOperation" class="mt-4">
        <div class="mb-3">
          <label for="value1" class="form-label">Valeur 1</label>
          <input v-model.number="valeuu1" type="number" class="form-control" id="value1" />
        </div>
        <div class="mb-3">
          <label for="value2" class="form-label">Valeur 2</label>
          <input v-model.number="valeur2" type="number" class="form-control" id="value2" />
        </div>
      </div>
  
      <!-- Bouton pour effectuer le calcul (affiché uniquement après sélection d'une opération) -->
      <button v-if="selectedOperation" @click="calculate" class="btn btn-secondary  mt-3">Calculer</button>
  
      <!-- Affichage du résultat ou du message d'erreur -->
      <div class="mt-4">
        <div v-if="error" class="alert alert-danger">{{ error }}</div>
        <div v-else class="alert alert-primary" v-if="selectedOperation">Résultat : {{ result }}</div>
      </div>
    </div>
  </template>
  
  <script setup>
  import { ref } from 'vue';
  
  // Déclaration des opérations possibles
  const operations = ['Addition', 'Multiplication', 'Division', 'Soustraction'];
  
  // Variables pour stocker l'opération sélectionnée, les valeurs entrées, le résultat et l'erreur
  const selectedOperation = ref('');
  const valeur1 = ref(0);
  const valeur2 = ref(0);
  const result = ref(0);
  const error = ref('');
  
  // Fonction pour effectuer le calcul en fonction de l'opération sélectionnée
  const calculate = () => {
    error.value = '';  // Réinitialiser les erreurs
    switch (selectedOperation.value) {
      case 'Addition':
        result.value = valeur1.value + valeur2.value;
        break;
      case 'Multiplication':
        result.value = valeur1.value * valeur2.value;
        break;
      case 'Division':
        if (value2.value === 0) {
          error.value = 'Division par zéro impossible.';
        } else {
          result.value = valeur1.value / valeur2.value;
        }
        break;
      case 'Soustraction':
        result.value = valeur1.value - valeur2.value;
        break;
      default:
        error.value = 'Opération non reconnue.';
    }
  };
  </script>
  
  <style scoped>
  .container {
    max-width: 700px;
  }
  </style>
  