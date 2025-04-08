<template>
  <aside class="bg-base-200 w-72 min-h-screen">
    <h2 class="text-lg font-bold mx-4">Proyectos</h2>
    <p class="text-sm font-bold mx-4">No hay proyectos</p>

    <ul class="menu ml-3 mt-4 p-3">
      <li><a>Item 1</a></li>
      <li>
        <details open>
          <summary>Parent</summary>
          <ul>
            <li class="ml-5"><a>Submenu 1</a></li>
            <li class="ml-5"><a>Submenu 2</a></li>
            <li>
              <details open>
                <summary>Parent</summary>
                <ul>
                  <li class="ml-5"><a>Submenu 1</a></li>
                  <li class="ml-5"><a>Submenu 2</a></li>
                </ul>
              </details>
            </li>
          </ul>
        </details>
      </li>
      <li><a>Item 2</a></li>
    </ul>
  </aside>
</template>

<script lang="ts" setup></script>
