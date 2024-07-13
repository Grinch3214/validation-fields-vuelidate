<script setup lang="ts">
import { ref } from "vue";
// import BaseCheckbox from "./components/BaseCheckbox.vue";
import BaseTagsInput from "./components/BaseTagsInput.vue";
import BaseInput from "./components/BaseInput.vue";

const is_checked = ref(false);
const tags = ref(["example"]);
</script>

<template>
  <div class="container my-10">
    <form class="max-w-[760px] mx-auto p-5 rounded shadow-md border">
      <!-- <BaseCheckbox v-model:checked="is_checked" /> -->
      <BaseInput
        type="text"
        id="first_name"
        label="First Name"
        required-symbol
      />
      <BaseInput type="text" id="last_name" label="Last Name" required-symbol />
      <BaseInput type="email" id="email" label="Email" required-symbol />
      <BaseInput
        type="password"
        id="password"
        label="Password"
        required-symbol
      />
      <BaseTagsInput
        v-model="tags"
        required-symbol
        label="Skills"
        placeholder="Vue.js, css, React, ets"
      />

      <div class="mt-6 text-end">
        <button
          @click.prevent
          class="py-1.5 px-10 bg-zinc-700 text-white rounded uppercase hover:bg-zinc-600 transition-colors"
        >
          Send
        </button>
      </div>
    </form>
  </div>
</template>
