<script setup lang="ts">
import AppModal from "./components/AppModal.vue";
import {ref} from "vue";

const isOpen = ref(false)
const isOpen2 = ref(false)


const openModal = () => isOpen.value = true
const closeModal = () => isOpen.value = false
const openModal2 = () => isOpen2.value = true
const closeModal2 = () => isOpen2.value = false


</script>

<template>
  <div class="app_header">
    <h3>Example modal window on Vue3</h3>
  </div>

  <button class="button" @click="openModal()">Open Modal</button>
  <AppModal v-if="isOpen"
            @closeModal="closeModal"
            :title="'This is my modal - draggable'"
            draggable
            resizable>
    <p>
      Lorem ipsum dolor, sit amet consectetur adipisicing elit. Dolores itaque
      inventore dignissimos suscipit delectus, ipsa repellat minima et vitae
      perspiciatis quasi unde earum corporis labore at in temporibus repudiandae
      totam
    </p>

  </AppModal>


  <button class="button" @click="openModal2()">Open Modal 2</button>
  <AppModal v-if="isOpen2"
            @closeModal="closeModal2"
            draggable
            :width="550"
            :top="400">
    <h3> You can open another modal window from here.</h3>
    <button class="button" @click="openModal()">Open Modal</button>
  </AppModal>


  <ul>
    <h3>All parameters are optional:</h3>
    <li>title</li>
    <li>width</li>
    <li>top</li>
    <li>draggable</li>
    <li>resizable</li>
  </ul>

</template>
