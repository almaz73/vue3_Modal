<script setup lang="ts">
import {computed} from "vue";

interface Props {
  width?: number;
  top?: number
}

const {width, top} = defineProps<Props>()
const emits = defineEmits(['closeModal'])

const defaultWidth = 400
const panelWidth = computed(() => width ? (width + 'px') : (defaultWidth + 'px'))
const panelTop = computed(() => top != undefined ? (top + 'px') : '100px')
const panelCenter = computed(() => (document.body.clientWidth / 2 - (width ? width : defaultWidth) / 2 - 10 + 'px'))
let dragObject = {elem: null, x: 0, y: 0};

function mousedown(e) {
  if (e.which != 1) return false; // если клик правой кнопкой мыши
  let elem = e.target.closest('.draggable');
  if (!elem) return false;
  dragObject.elem = elem
  dragObject.x = e.offsetX;
  dragObject.y = e.offsetY;
}

document.onmousemove = function (e) {
  if (!dragObject.elem) return;
  dragObject.elem.style.left = e.pageX - dragObject.x + 'px';
  dragObject.elem.style.top = e.pageY - dragObject.y + 'px';
}
const mouseup = () => dragObject.elem = null


</script>
<template>
  <Teleport to="body">
    <div class="modal">
      <div class="modal__fon" @click="emits('closeModal')"></div>
      <div class="modal__content draggable">
        <div class="modal__head"
             @mouseup="mouseup"
             @mousedown="mousedown"></div>
        <div class="modal__title">
          <h2>This is my modal</h2>
        </div>
        <div class="close_cross" @click="emits('closeModal')">❌</div>
        <div class="modal__info">
          <slot/>
        </div>
      </div>
    </div>
  </Teleport>
</template>
<style>
.modal {
  top: 0;
  width: 100%;
  height: 100vh;
  position: fixed;
}

.modal__fon {
  width: 100%;
  height: 100vh;
  background: black;
  opacity: .5;
}

.modal__head {
  position: absolute;
  width: calc(100% - 35px);
  height: 30px;
  background: yellow;
  top: 0;
  left: 0;
  opacity: 0;
  cursor: pointer;
}

.modal__content {
  position: absolute;
  background: pink;
  width: v-bind(panelWidth);
  top: v-bind(panelTop);
  left: v-bind(panelCenter);
  padding: 10px;
  border-radius: 10px;
  box-shadow: 0 0 5px black;
}

.close_cross {
  position: absolute;
  top: 5px;
  right: 5px;
  cursor: pointer;
}

.modal__title {
  background: blue;
}

.modal__info {
  background: green;
}
</style>