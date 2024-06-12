<script setup lang="ts">
defineProps({
  name: { type: String, default: '' },
});
</script>

<template>
  <transition-group
    tag="div"
    :name="name"
  >
    <slot />
  </transition-group>
</template>
