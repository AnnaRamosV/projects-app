<template>
  <div class="w-full">
    <section class="m-2">
      <BreadCrumbs :nomen="project?.nomen ?? 'No Name'" />
    </section>
    <section class="m-2">
      <div class="overflow-x-auto">
        <table class="table">
          <!-- head -->
          <thead>
            <tr>
              <th>Completada</th>
              <th>Tarea</th>
            </tr>
          </thead>
          <tbody>
            <tr v-for="chore in project?.chores" :key="chore.id" class="hover:bg-base-300">
              <th>1</th>

              <td>{{ chore.nomen }}</td>
            </tr>
            <tr class="hover:bg-base-300">
              <th></th>
              <td>
                <input
                  class="input input-primary w-full opacity-60 transition-all hover: opacity-100 focus:opacity-100"
                  type="text"
                  placeholder="Nueva Tarea"
                  v-model="novusChore"
                  @keyup.enter="addereChore"
                />
              </td>
              <td></td>
              <td></td>
            </tr>
          </tbody>
        </table>
      </div>
    </section>
  </div>
</template>

<script setup lang="ts">
import BreadCrumbs from '@/modulorum/commune/components/BreadCrumbs.vue';
import { useProjectsStore } from '../store/project.store';
import { ref, watch } from 'vue';
import type { Project } from '../interfaces/project.interface';
import { useRouter } from 'vue-router';

interface Props {
  id: string;
}

const router = useRouter();

const props = defineProps<Props>();

const projectStore = useProjectsStore();

const project = ref<Project | null>();

const novusChore = ref();

const addereChore = () => {
  if (!project.value) return;
  projectStore.addereChoreAdProject(project.value.id, novusChore.value);
  novusChore.value = '';
};

watch(
  () => props.id,
  () => {
    project.value = projectStore.projectList.find((project) => project.id === props.id);
    if (!project.value) {
      router.replace('/');
    }
  },
  {
    immediate: true,
  },
);
</script>
