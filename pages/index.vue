<template>
  <v-container>
    <v-row>
      <v-col cols="12">
        <v-text-field v-model="newTask" label="New Task" @keyup.enter="addTask"></v-text-field>
      </v-col>
      <v-col cols="12">
        <v-btn @click="addTask" color="primary">Add Task</v-btn>
      </v-col>
    </v-row>

    <v-row>
      <v-col cols="12" v-for="(task, index) in tasks" :key="index">
        <v-card>
          <v-card-title>
            {{ task }}
            <v-spacer></v-spacer>
            <v-btn icon @click="removeTask(index)">
              <v-icon>mdi-delete</v-icon>
            </v-btn>
          </v-card-title>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<script setup>
import { ref } from 'vue'

const newTask = ref('')
const tasks = ref([])

const addTask = () => {
  if (newTask.value.trim()) {
    tasks.value.push(newTask.value)
    newTask.value = ''
  }
}

const removeTask = (index) => {
  tasks.value.splice(index, 1)
}
</script>
