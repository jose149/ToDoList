<script setup lang="ts">
import { ref, watch } from "vue";

interface AppInputProps {
  checked: boolean;
  value: string;
}
interface AppInputEmits {
  (event: "input-changed", value: string): void;
  (event: "add-item"): void;
}
const props = withDefaults(defineProps<AppInputProps>(), { checked: false });
const emit = defineEmits<AppInputEmits>();

const itemText = ref<string>(props.value ?? "");

watch(itemText, () => {
  emit("input-changed", itemText.value);
});
</script>

<template>
  <div class="input-text" @keydown.enter="emit('add-item')">
    <input :class="{ checked: props.checked }" type="text" v-model="itemText" />
  </div>
</template>

<style scoped lang="scss">
.input-text {
  width: 100%;
  input {
    width: calc(100% - 25px);
    font-size: $font-size-secondary-desktop;
    color: $primary-text;
    background-color: transparent;
    border: none;
    &.checked {
      color: $secondary-text;
      text-decoration: line-through;
    }
    &:focus {
      outline: none;
    }
    @media only screen and (max-width: $medium-breackpoint) {
      font-size: $font-size-secondary-mobile;
    }
  }
}
</style>
