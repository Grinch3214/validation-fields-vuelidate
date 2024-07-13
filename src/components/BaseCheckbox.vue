<script setup lang="ts">
import { ref, computed } from "vue";
import { CheckboxIndicator, CheckboxRoot } from "radix-vue";
import { Icon } from "@iconify/vue";

const props = defineProps<{
  id?: string | number;
  label?: string;
  disabled?: boolean;
  checked?: boolean;
}>();

const emit = defineEmits(["update:checked"]);

const isCheckedLocal = computed({
  get: () => props.checked,
  set: (value) => emit("update:checked", value),
});
</script>

<template>
  <div class="flex flex-col gap-2.5">
    <label
      class="flex flex-row gap-4 items-center [&>.checkbox]:hover:bg-neutral-100"
    >
      <CheckboxRoot
        :disabled="disabled"
        v-model:checked="isCheckedLocal"
        @update:checked="$emit('update:checked', $event)"
        class="w-[20px] h-[20px] border border-black rounded-sm"
      >
        <CheckboxIndicator
          class="bg-white h-full w-full rounded flex items-center justify-center"
        >
          <Icon icon="radix-icons:check" class="h-3.5 w-3.5 text-grass11" />
        </CheckboxIndicator>
      </CheckboxRoot>
      <span class="select-none text-black">Accept terms and conditions.</span>
    </label>
  </div>
</template>
