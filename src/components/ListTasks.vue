<template>
    <div>
        <v-list lines="three" select-strategy="classic">
            <v-list-subheader>Tasks</v-list-subheader>
            <v-list-item v-for="(task, index) in taskStore.tasks" :key="task.value" :subtitle="task.subtitle"
                :title="task.title" :value="task.value" @click="taskStore.toggleDoneTask(index)">
                <template v-slot:prepend="{  }">
                    <v-list-item-action start>
                        <v-checkbox-btn :model-value="task.done"></v-checkbox-btn>
                    </v-list-item-action>
                </template>
                <template v-slot:append>
                    <v-menu>
                        <template v-slot:activator="{ props }">
                            <v-btn color="grey-lighten" icon="mdi-dots-vertical" variant="text" v-bind="props"></v-btn>
                        </template>
                        <v-list>
                            <v-list-item @click="taskStore.toggleEdit(index)">
                                <v-list-item-title>Editar</v-list-item-title>
                            </v-list-item>
                            <v-list-item @click="taskStore.toggleDelete(index)">
                                <v-list-item-title>Deletar</v-list-item-title>
                            </v-list-item>
                        </v-list>
                    </v-menu>

                </template>
            </v-list-item>
        </v-list>

        <DialogTaskFields :task="taskStore.tasks[taskStore.indexTaskSelected]" />
        <DialogDelete />

    </div>
</template>

<script setup>
import DialogTaskFields from './dialogs/DialogTaskFields.vue'
import DialogDelete from './dialogs/DialogDelete.vue'
import { useTaskStore } from '@/stores/task'

const taskStore = useTaskStore()

</script>