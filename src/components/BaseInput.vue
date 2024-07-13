<template>
  <div>
    <label v-if="label" :for="id?.toString()" class="block text-xs"
      >{{ label }}
      <span v-show="requiredSymbol" class="text-sm text-red-400">*</span></label
    >
    <input
      v-model="model"
      :type="type"
      :id="id?.toString()"
      class="border rounded w-full px-2 py-[5px]"
    />
  </div>
</template>

<script setup lang="ts">
const props = withDefaults(
  defineProps<{
    type: string;
    id?: string | number;
    label?: string;
    requiredSymbol?: boolean;
  }>(),
  {
    type: "text",
    requireSymbol: false,
  }
);

const model = defineModel<string>();
</script>
