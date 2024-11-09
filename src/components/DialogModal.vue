<script setup>
import { ref, watch } from 'vue';
import {
  Dialog,
  DialogContent,
  DialogFooter,
  DialogHeader,
  DialogTitle,
} from '@/components/ui/dialog';
import { MultiSelect } from '@/components/ui/multi-select';

const selectedOptions = ref([]);
const selectOptions = [
  { label: 'Option 1', value: '1' },
  { label: 'Option 2', value: '2' },
];

const showModal = defineModel('showModal');
</script>

<template>
  <Dialog v-model:open="showModal">
    <DialogContent
      class="sm:max-w-xl grid-rows-[auto_minmax(0,1fr)_auto] p-0 max-h-[80dvh]"
      @interactOutside="(e) => e.preventDefault()"
    >
      <DialogHeader class="p-6 pb-0">
        <DialogTitle>Add Form</DialogTitle>
      </DialogHeader>
      <div class="grid gap-4 py-4 overflow-y-auto px-6">
        <div class="flex flex-col justify-between">
          <form id="add-record" @submit="onSubmit">
            <div class="mb-4 mt-2">
              <div class="w-1/2">
                <MultiSelect
                  placeholder="Select"
                  :options="selectOptions"
                  v-model:modelValue="selectedOptions"
                />
              </div>
            </div>
          </form>
        </div>
      </div>
      <DialogFooter class="p-6 pt-0">
        <div class="px-4 py-3 text-right">
          <button
            form="add-record"
            type="submit"
            class="bg-green1 text-base font-medium text-white w-[139px] rounded-3xl px-6 py-2"
          >
            Add
          </button>
        </div>
      </DialogFooter>
    </DialogContent>
  </Dialog>
</template>
