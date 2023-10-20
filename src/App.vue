<script setup lang="ts">
import AppModal from "./components/AppModal.vue";
import {ref} from "vue";

const isOpen = ref(true)



function openModal() {
  isOpen.value = true
}

function closeModal() {
  isOpen.value = false
}

</script>

<template>
  <div class="app_header">
    <h3>Example modal window on Vue3</h3>
  </div>

  <button class="button" @click="openModal()">Open Modal</button>
  <AppModal v-if="isOpen"
            @closeModal="closeModal"
            :width="350"
            :top="200">
    <p>
      Lorem ipsum dolor, sit amet consectetur adipisicing elit. Dolores itaque
      inventore dignissimos suscipit delectus, ipsa repellat minima et vitae
      perspiciatis quasi unde earum corporis labore at in temporibus repudiandae
      totam
    </p>
  </AppModal>


  <main class="app-main">
  </main>
</template>
