<script setup lang="ts">
import { ref } from "vue";
import BaseCheckbox from "./components/BaseCheckbox.vue";
import BaseTagsInput from "./components/BaseTagsInput.vue";

const is_checked = ref(false);
const tags = ref(["example"]);
</script>

<template>
  <div class="container">
    <BaseCheckbox v-model:checked="is_checked" />
    <BaseTagsInput v-model="tags" />
  </div>
</template>
