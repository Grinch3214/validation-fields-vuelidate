<template>
  <div>
    <p v-if="label" class="block text-xs">
      {{ label }}
      <span v-show="requiredSymbol" class="text-sm text-red-400">*</span>
    </p>
    <TagsInputRoot
      v-model="model"
      class="flex gap-2 items-center border p-1 rounded-lg w-full flex-wrap bg-white min-h-[32px]"
    >
      <TagsInputItem
        v-for="item in model"
        :key="item"
        :value="item"
        class="text-black text-xs border bg-zinc-200 flex items-center justify-center gap-2 rounded"
      >
        <TagsInputItemText class="text-sm pl-1" />
        <TagsInputItemDelete class="p-0.5 rounded bg-transparent">
          <Icon icon="lucide:x" />
        </TagsInputItemDelete>
      </TagsInputItem>

      <TagsInputInput
        :placeholder="placeholder"
        class="text-sm focus:outline-none flex-1 rounded bg-transparent px-1"
      />
    </TagsInputRoot>
  </div>
</template>

<script setup lang="ts">
import {
  TagsInputInput,
  TagsInputItem,
  TagsInputItemDelete,
  TagsInputItemText,
  TagsInputRoot,
} from "radix-vue";
import { Icon } from "@iconify/vue";

const props = defineProps<{
  label?: string;
  requiredSymbol?: boolean;
  inputClass?: string;
  placeholder?: string;
}>();

const model = defineModel<string[]>();
</script>
