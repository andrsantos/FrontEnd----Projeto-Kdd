<script setup>
import { defineProps, defineEmits } from 'vue';

defineProps({
  predictedCargo: {
    type: String,
    required: true
  }
});

defineEmits(['close', 'back']);
</script>

<template>
  <div class="modal-overlay" @click.self="$emit('close')">

    <div class="card modal-card">

      <div class="button-far-left">
        <button class="close-button" @click="$emit('close')">X</button>
      </div>
      <header class="modal-header">
        <h2 class="text-gradient">Resultado da Predição</h2>
      </header>
      
      <div class="modal-content">

        <div class="icon-section">
          <p class="celebration-icon">🎉</p>
        </div>
        <p class="prediction-text">
          O cargo mais provável para você é:
          <span class="predicted-cargo">{{ predictedCargo }}</span>
        </p>
      </div>

      <div class="form-actions">
        <button class="card-button-secondary" @click="$emit('back')">
          Voltar ao formulário
        </button>
      </div>

    </div>

  </div>
</template>

<style scoped>
.modal-overlay {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5);
  display: flex;
  justify-content: center;
  align-items: center;
  z-index: 1000;
}

.icon-section {
  display:flex;
  justify-content: center;
  align-items: center;
  margin-bottom:2%;
}

.modal-card {
  position: relative;
  padding: 2rem;
  min-width: 450px;
  max-width: 700px;
  max-height: 80vh;
  overflow-y: auto;
  text-align: center;
}

.modal-header {
  display: flex;
  justify-content: center;
  align-items: center;
  margin-bottom: 20px;
}

.close-button {
  background: none;
  border: none;
  font-size: 1.5rem;
  cursor: pointer;
  display:flex;
}

.modal-content {
  margin-bottom: 20px;
}

.prediction-text {
  font-size: 1.25rem;
  color: var(--color-primary);
}

.predicted-cargo {
  display: block;
  font-size: 1.75rem;
  font-weight: 700;
  color: var(--color-link);
  margin-top: 0.5rem;
}

.form-actions {
  margin-top: 20px;
  text-align: center;
}

.button-far-left {
  display:flex;
  justify-content: flex-end;
}
.celebration-icon {
  font-size: 3rem;
  margin: 1rem 0;
  display:flex;
}
</style>