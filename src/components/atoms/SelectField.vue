<!-- src/components/SelectField.vue -->
<template>
  <div class="mb-3">
    <label :for="id" class="form-label mx-1">{{ label }}</label>
    <select :id="id" class="form-select" :value="modelValue" @input="updateValue">
      <option disabled value="">{{ placeholder }}</option>
      <option v-for="option in options" :key="option.value" :value="option.value">
        {{ option.text }}
      </option>
    </select>
  </div>
</template>

<script setup lang="ts">
import { defineProps, defineEmits } from 'vue';

defineProps<{
  id: string;
  label: string;
  options: { value: string; text: string }[];
  modelValue: string;
  placeholder: string;
}>();

const emits = defineEmits(['update:modelValue']);

const updateValue = (event: Event) => {
  emits('update:modelValue', (event.target as HTMLSelectElement).value);
};
</script>

<style scoped>
.form-select {
  border-radius: 50px;
}
</style>

