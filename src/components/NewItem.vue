<script setup lang="ts">
import AppButton from "./AppButton.vue";
import { ref } from "vue";

interface AppButtonEmits {
  (event: "add-item", value: string): void;
}
const emit = defineEmits<AppButtonEmits>();
const itemText = ref<string>("");

function addItem(): void {
  if (itemText.value === "") {
    return;
  }
  emit("add-item", itemText.value);
  itemText.value = "";
}
</script>

<template>
  <div class="item-container">
    <div class="input-text" @keydown.enter="addItem">
      <input type="text" placeholder="Type here" v-model="itemText" />
    </div>
    <AppButton :disabled="itemText === ''" @add-item="addItem" />
  </div>
</template>

<style scoped lang="scss">
.item-container {
  background-color: $background-4;
  height: 50px;
  width: 100%;
  border-radius: 10px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 0 10px 0 25px;
  @media only screen and (max-width: $medium-breackpoint) {
    background-color: transparent;
    height: 40px;
  }
  .checked-icon {
    margin: 10px 20px;
  }
  .close-icon {
    margin: 15px;
  }
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
}
</style>
