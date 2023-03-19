<template>
  <header class="header-flex-container">
    <div>
      <svg version="1.1" viewBox="0 0 220 72" class="svg-icon svg-fill header-svg">
        <g fill-rule="nonzero" fill="none">
          <g opacity=".9">
            <path pid="0" :d="headerSvgDrawAttrs[0]" fill="#364FDE">
            </path>
            <path pid="1" :d="headerSvgDrawAttrs[1]" fill="#56D8FF">
            </path>
            <path pid="2" :d="headerSvgDrawAttrs[2]" fill="#667DFF">
            </path>
          </g>
        </g>
      </svg>
    </div>
    <div class="header-text-container">
      <div class="header-text-1">VueSchool Demo</div>
      <div class="header-text-2">(by George Jempty)</div>
    </div>
  </header>
</template>

<script setup>
import { defineProps } from "vue";
const props = defineProps({
  // headerSvgDrawAttrs: Array
  headerSvgDrawAttrs: {
    type: Array,
    required: true
  }
});
</script>

<style scoped>
.header-flex-container {
  display: flex;
  justify-content: center;
}
.header-svg {
  height: 3rem;
}

.header-text-container {
  margin-left: -5rem; 
  padding-top: 0.25rem;
  vertical-align: top;
}

.header-text-1 {
  font-size: 2rem;
}
.header-text-2 {
  font-size: 1.5rem;
  text-align: center;
}
</style>