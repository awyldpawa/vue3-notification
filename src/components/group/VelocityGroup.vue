<script setup lang="ts">
defineProps({
  name: { type: String, default: '' },
});

const emit = defineEmits<{
  (eventName: 'enter', element: Element, done: () => void): void,
  (eventName: 'leave', element: Element, done: () => void): void,
  (eventName: 'afterLeave'): void
}>();

const handleEnter = (element: Element, done: () => void) => {
  emit('enter', element, done);
};

const handleLeave = (element: Element, done: () => void) => {
  emit('leave', element, done);
};

const handleAfterLeave = () => {
  emit('afterLeave');
};
</script>

<template>
  <transition-group
    tag="div"
    :css="false"
    :name="name"
    @on-enter="handleEnter"
    @on-leave="handleLeave"
    @on-after-leave="handleAfterLeave"
  >
    <slot />
  </transition-group>
</template>
