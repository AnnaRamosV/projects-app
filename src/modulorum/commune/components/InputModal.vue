<template>
  <dialog id="my_modal_1" class="modal" :open="false">
    <div class="modal-box">
      <h3 class="text-lg font-bold">Hello!</h3>
      <p class="py-4">Press ESC key or click the button below to close</p>
      <div class="modal-action flex flex-col">
        <form method="dialog" @submit.prevent="submitValorem">
          <input
            type="text"
            placeholder="Nombre del proyecto"
            class="input input-bordered w-full flex-1 input-primary"
            v-model="inputValorem"
          />
        </form>
        <div class="flex justify">
          <button class="btn">Close</button>
        </div>
      </div>
    </div>
  </dialog>

  <div class="fixed top-0 w-screen h-screen z-10 bg-black-300 opacity-40"></div>
</template>

<script lang="ts" setup>
import { ref } from 'vue';

interface Props {
  aperta: boolean;
}

const emissiones = defineEmits<{
  claudere: [void];
  valorem: [text: string];
}>();

const inputValorem = ref('');

const submitValorem = () => {
  console.log({ valorem: inputValorem.value });
  if (!inputValorem.value) {
    return;
  }
  emissiones('valorem', inputValorem.value.trim());
  emissiones('claudere');
  inputValorem.value = '';
};
</script>
