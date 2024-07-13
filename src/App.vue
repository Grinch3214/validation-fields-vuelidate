<script setup lang="ts">
import { ref } from "vue";
import BaseCheckbox from "./components/BaseCheckbox.vue";
import BaseTagsInput from "./components/BaseTagsInput.vue";
import BaseInput from "./components/BaseInput.vue";

const is_checked = ref(false);
const tags = ref(["example"]);
</script>

<template>
  <div class="container">
    <BaseCheckbox v-model:checked="is_checked" />
    <BaseTagsInput v-model="tags" />
    <BaseInput type="text" id="25" label="Name" require-symbol />
  </div>
</template>
