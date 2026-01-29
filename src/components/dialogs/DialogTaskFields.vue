<template>
  <div class="text-center pa-4">
    <v-dialog
      v-model="taskStore.showDialogTaskFields"
      min-width="400"
      max-width="600"
      persistent
    >
      <v-card title="Edit Task">
        <v-card-text>
            <v-text-field label="Title" v-model="props.task.title"></v-text-field>
            <v-text-field label="Description" v-model="props.task.subtitle"></v-text-field>
        </v-card-text>
        <v-card-actions>
          <v-spacer></v-spacer>
          <v-btn color="primary" variant="elevated" @click="taskStore.updateTask">
            Ok
          </v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
  </div>
</template>

<script setup>
import { defineProps } from 'vue'
import { useTaskStore } from '@/stores/task'

const taskStore = useTaskStore()
const props = defineProps({
task: Object
})
</script>