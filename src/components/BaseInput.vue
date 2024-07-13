<template>
  <div>
    <label v-if="label" :for="id?.toString()" class="block text-xs"
      >{{ label }}
      <span v-show="requiredSymbol" class="text-sm text-red-400">*</span></label
    >
    <input
      :type="type"
      :id="id?.toString()"
      class="border rounded w-full h-[32px]"
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
</script>
