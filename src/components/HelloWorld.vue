<script setup>
import { ref } from 'vue';
import DialogModal from '@/components/DialogModal.vue';
import { Button } from '@/components/ui/button';
import { MultiSelect } from '@/components/ui/multi-select';
defineProps({
  msg: String,
});

const show = ref(false);
const selectedOptions = ref([]);
const selectOptions = [
  { label: 'Option 1', value: '1' },
  { label: 'Option 2', value: '2' },
];
</script>

<template>
  <div class="flex flex-col item-center justify-center p-8">
    <div class="w-1/2">
      <MultiSelect
        placeholder="Select Sensors"
        :options="selectOptions"
        v-model="selectedOptions"
      />
    </div>
    <div class="mt-4">
    <Button @click="show = true">Open Dialog</Button>
  </div>
  </div>
  <DialogModal v-model:showModal="show" />
</template>
