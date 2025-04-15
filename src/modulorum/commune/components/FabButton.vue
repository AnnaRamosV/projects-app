<template>
  <button
    @click="$emit('click')"
    :class="['btn btn-circle btn-secondary fixed z-9999', positionClasses]"
  >
    <slot />
  </button>
</template>

<script setup lang="ts">
import { computed } from 'vue';
import { defineProps } from 'vue';

const props = defineProps<{
  positione: 'bottom-right' | 'bottom-left' | 'top-right' | 'top-left';
}>();

const positionClasses = computed(() => {
  switch (props.positione) {
    case 'bottom-right':
      return 'fixed bottom-4 right-4';
    case 'bottom-left':
      return 'fixed bottom-4 left-4';
    case 'top-right':
      return 'fixed top-4 right-4';
    case 'top-left':
      return 'fixed top-4 left-4';
    default:
      return '';
  }
});
</script>
