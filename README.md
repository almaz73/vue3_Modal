# Vue 3 + TypeScript + Vite

This template should help get you started developing with Vue 3 and TypeScript in Vite. The template uses Vue
3 `<script setup>` SFCs, check out
the [script setup docs](https://v3.vuejs.org/api/sfc-script-setup.html#sfc-script-setup) to learn more.

## Simple Modal Window :

### all parametrs are optional:

content + title + top + width + draggable + resizible

## Нow to use:
~~~
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
~~~

# Demo 
https://fmap.ru/games/modal



