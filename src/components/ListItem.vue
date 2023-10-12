<script setup lang="ts">
import { ref } from "vue";
import AppInput from "./AppInput.vue";
interface ListItemProps {
  value: string;
}
interface ListItemEmits {
  (event: "remove"): void;
}
defineProps<ListItemProps>();
const emit = defineEmits<ListItemEmits>();

const checked = ref<boolean>(false);
function toggleChecked(): void {
  checked.value = !checked.value;
}
</script>

<template>
  <div class="item-container">
    <div class="checked-icon" @click="toggleChecked">
      <img v-if="checked" src="@/assets/checked.svg" />
      <img v-else src="@/assets/unchecked.svg" />
    </div>
    <AppInput :checked="checked" :value="value" />
    <div class="remove-icon" @click="emit('remove')">
      <img src="@/assets/cross.svg" />
    </div>
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
  @media only screen and (max-width: $medium-breackpoint) {
    height: 40px;
  }
  .checked-icon {
    margin: 10px 20px;
    user-select: none;
    @media only screen and (max-width: $medium-breackpoint) {
      img {
        width: 25px;
      }
    }
  }
  .remove-icon {
    margin: 15px;
    user-select: none;
    @media only screen and (max-width: $medium-breackpoint) {
      img {
        width: 15px;
      }
    }
  }
  .checked-icon:hover,
  .remove-icon:hover {
    cursor: pointer;
  }
}
</style>
