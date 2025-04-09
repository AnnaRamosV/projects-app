<template>
  <button
    @click="$emit('click')"
    class="['btn btn-circle btn-secondary fixed', positione]"
  ></button>
</template>

<script lang="ts" setup>
interface Props {
  positione: 'top-left' | 'top-right' | 'bottom-left' | 'bottom-right';
}

withDefaults(defineProps<Props>(), {
  positione: 'bottom-right',
});

defineEmits(['click']);
</script>

<style scoped>
@import 'tailwindcss';

.top-left {
  top: 10;
  left: 10;
}

.top-right {
  top: 10;
  right: 10;
}

.bottom-left {
  bottom: 10;
  left: 10;
}

.bottom-right {
  bottom: 10;
  right: 10;
}
</style>
