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
    <form class="max-w-[760px] mx-auto p-5 rounded shadow-md">
      <!-- <BaseCheckbox v-model:checked="is_checked" /> -->
      <BaseTagsInput v-model="tags" required-symbol label="Emails" />
      <BaseInput type="text" id="25" label="Name" required-symbol />
    </form>
  </div>
</template>
