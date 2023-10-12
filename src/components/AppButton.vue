<script setup lang="ts">
interface AppButtonProps {
  disabled: boolean;
}
interface AppButtonEmits {
  (event: "add-item"): void;
}
defineProps<AppButtonProps>();
const emit = defineEmits<AppButtonEmits>();
</script>
<template>
  <button
    :disabled="disabled"
    class="button-container"
    :class="{ disabled: disabled }"
    @click="emit('add-item')"
  >
    <p class="button-text">Add</p>
  </button>
</template>

<style scoped lang="scss">
button {
  all: unset;
  transition: all 0.2s ease;
}
.button-container {
  width: 100px;
  height: 40px;
  background-color: $primary;
  color: $primary-text;
  border-radius: 10px;
  display: flex;
  align-items: center;
  justify-content: center;
  &:disabled {
    background-color: $secondary-text;
    color: $background-1;
    &:hover {
      cursor: default;
    }
  }
  &:hover {
    cursor: pointer;
  }
  .button-text {
    font-weight: 600;
    user-select: none;
  }
}
</style>
