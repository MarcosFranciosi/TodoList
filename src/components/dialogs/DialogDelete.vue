<template>
  <div class="text-center pa-4">
    <v-dialog
      v-model="taskStore.showDialogDelete"
      min-width="400"
      max-width="600"
      persistent
    >
      <v-card>
        <v-card-title class="text-h5">
            Are you sure you want delete this task?
        </v-card-title>
        <v-card-text>
            This action can't be reverted..
        </v-card-text>
        <v-card-actions>
          <v-spacer></v-spacer>
          <v-btn color="red-darken-1" variant="elevated" @click="taskStore.toggleDelete">
            No
          </v-btn>
          <v-btn color="red-darken-1" variant="outlined" @click="taskStore.deleteTask">
            Yes
          </v-btn>
        </v-card-actions>
      </v-card>
    </v-dialog>
  </div>
</template>

<script setup>
import { useTaskStore } from '@/stores/task'

const taskStore = useTaskStore()

</script>