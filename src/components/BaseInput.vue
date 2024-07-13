<template>
  <div>
    <label v-if="label" :for="id?.toString()" class="block text-xs"
      >{{ label }}
      <span v-show="requireSymbol" class="text-sm text-red-400">*</span></label
    >
    <input :type="type" :id="id?.toString()" class="border rounded w-full" />
  </div>
</template>

<script setup lang="ts">
const props = withDefaults(
  defineProps<{
    type: string;
    id?: string | number;
    label?: string;
    requireSymbol?: boolean;
  }>(),
  {
    type: "text",
    requireSymbol: false,
  }
);
</script>
