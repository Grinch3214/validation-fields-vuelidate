<template>
  <div class="container my-10 text-sm">
    <form
      @submit.prevent="onSubmit"
      class="max-w-[760px] mx-auto p-5 rounded shadow-md border grid gap-2"
    >
      <!-- <BaseCheckbox v-model:checked="is_checked" /> -->
      <div :class="{ error: v$.formData.firstName.$errors.length }">
        <BaseInput
          v-model="formData.firstName"
          type="text"
          id="first_name"
          label="First Name"
          required-symbol
        />
        <div
          class="input-errors"
          v-for="error of v$.formData.firstName.$errors"
          :key="error.$uid"
        >
          <div class="error-msg">{{ error.$message }}</div>
        </div>
      </div>
      <BaseInput
        v-model="formData.lastName"
        type="text"
        id="last_name"
        label="Last Name"
        required-symbol
      />
      <BaseInput
        v-model="formData.email"
        type="email"
        id="email"
        label="Email"
        required-symbol
      />
      <BaseInput
        v-model="formData.password"
        type="password"
        id="password"
        label="Password"
        required-symbol
      />
      <BaseTagsInput
        v-model="formData.tags"
        required-symbol
        label="Skills"
        placeholder="Vue.js, css, React, ets"
      />

      <div class="mt-6 text-end">
        <button
          class="py-1.5 px-10 bg-zinc-700 text-white rounded uppercase hover:bg-zinc-600 transition-colors"
        >
          Send
        </button>
      </div>
    </form>
  </div>
</template>

<script setup lang="ts">
import { ref } from "vue";
// import BaseCheckbox from "./components/BaseCheckbox.vue";
import BaseTagsInput from "./components/BaseTagsInput.vue";
import BaseInput from "./components/BaseInput.vue";
import { useVuelidate } from "@vuelidate/core";
import { required, email } from "@vuelidate/validators";

const formData = ref({
  firstName: "",
  lastName: "",
  email: "",
  password: "",
  tags: [],
});

const rules = {
  formData: {
    firstName: { required },
    lastName: { required },
    email: { required, email },
    password: { required },
    tags: { required },
  },
};

const v$ = useVuelidate(rules, formData);

console.log(v$.value.formData);

async function onSubmit() {
  const result = await v$.value.$validate();

  console.log(result);
  const tags = formData.value.tags.map((i) => i);

  const data = {
    firstName: formData.value.firstName,
    lastName: formData.value.lastName,
    email: formData.value.email,
    password: formData.value.password,
    tags: tags,
  };

  console.log(data);
}
</script>
