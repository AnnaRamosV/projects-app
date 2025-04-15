<template>
  <div class="overflow-x-auto w-full">
    <table class="table">
      <!-- head -->
      <thead>
        <tr>
          <th></th>
          <th>Proyectos</th>
          <th>Tareas</th>
          <th>Avance</th>
        </tr>
      </thead>
      <tbody>
        <!-- row 2 -->
        <tr
          v-for="(project, index) in projectStore.projectList"
          :key="project.id"
          class="hover:bg-base-300"
        >
          <th>{{ index + 1 }}</th>
          <td>{{ project.nomen }}</td>
          <td>{{ project.chores.length }}</td>
          <td>Purple</td>
          <progress class="progress progress-primary w-56" value="10" max="100"></progress>
        </tr>
      </tbody>
    </table>
  </div>

  <InputModal
    :aperta="modalAperta"
    @claudere="modalAperta = false"
    @valorem="projectStore.addereProject"
    placeholder="Introduce el nombre del proyecto"
    titulus="Nuevo proyecto"
    subtitulus="Dale un nombre a tu proyecto"
  />

  <propium-modal :aperta="propiumModalAperta">
    <template #header>
      <h1 class="text-3xl">Título del modal</h1>
    </template>
    <template #body>
      <p>
        Lorem ipsum dolor sit, amet consectetur adipisicing elit. Hic vitae corrupti debitis
        excepturi officia modi error, quod accusantium pariatur consequatur assumenda veniam! Qui
        sit dolorum fuga error saepe, pariatur omnis!
      </p>
    </template>
    <template #footer>
      <div class="flex justify-end">
        <button @click="propiumModalAperta = false" class="btn">Close</button>
        <button @click="propiumModalAperta = false" class="btn btn-primary ml-4">Aceptar</button>
      </div>
    </template>
  </propium-modal>

  <fab-button
    positione="bottom-right"
    class="fixed bottom-4 right-4 z-50"
    @click="modalAperta = true"
  >
    <AddCircle />
  </fab-button>

  <fab-button positione="bottom-left" @click="propiumModalAperta = true">
    <ModalIcon />
  </fab-button>
</template>
<script lang="ts" setup>
import FabButton from '@/modulorum/commune/components/FabButton.vue';
import InputModal from '@/modulorum/commune/components/InputModal.vue';
import PropiumModal from '@/modulorum/commune/components/PropiumModal.vue';
import AddCircle from '@/modulorum/commune/icons/AddCircle.vue';
import ModalIcon from '@/modulorum/commune/icons/ModalIcon.vue';
import { ref } from 'vue';
import { useProjectsStore } from '../store/project.store';

const modalAperta = ref(false);

const propiumModalAperta = ref(false);

const projectStore = useProjectsStore();
</script>
