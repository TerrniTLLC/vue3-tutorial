<template>
  <div class="p-9 bg-zinc-600/90">
    <div class="flex flex-col bg-zinc-900 rounded-md py-4 gap-2 w-[340px] mt-3">

      <!-- Задача 2: Разбить на компоненты -->
      <h1 class="text-white text-xl font-medium px-4">Create Task</h1>

      <!-- Задача 2: Разбить на компон9нты -->
      <div class="border-t border-b border-zinc-700">
        <div class="my-2 gap-y-2 flex flex-col px-4 py-5">
          <!-- Задача 1: Сделать так чтобы можно было вводить значения и создавать тудушку -->
          <label class="text-white text-[12px] font-medium">Name</label>
          <input name="Name" type="text"
            class="border text-[12px] rounded border-zinc-700 bg-zinc-900/90 text-zinc-200 h-8" v-model="data.name" />
        </div>
      </div>

      <!-- Задача 2: Разбить на компоненты -->
      <div class="flex gap-x-2 text-[12px] px-4 pt-2">
        <h3 class="text-white">Checklist</h3>
        <!-- Задача 3: Отрисуй выполненные и все задачи -->
        <span class="text-zinc-400">{{ completedTodos }}/{{ totalTodos }}</span>
        <!-- Задача 3: Отрисуй выполненные и все задачи -->

        <!-- Задача 1: Сделать так чтобы можно было вводить значения и создавать тудушку -->
        <button class="text-blue-500 ml-4 font-medium hover:text-blue-600" @:click="addNewTodo()">Add Item</button>
      </div>

      <!-- Задача 2: Разбить на компоненты -->
      <div class="flex flex-col px-4">
        <div v-for="todo in todos" :key="todo.name" class="flex gap-x-2 mt-2 items-center">
          <input type="checkbox" v-model="todo.isChecked" class="rounded-[4px] bg-zinc-900/80 text-blue-500" />
          <div class="flex flex-col">
            <span class="text-zinc-200 text-[12px]">{{ todo.name }}</span>
          </div>
          <button class="text-red-500 bg-transparent hover:bg-red-500/20 rounded" @:click="removeTodoById(todo.id)">
            <svg xmlns="http://www.w3.org/2000/svg" class="h-4 w-4" viewBox="0 0 15 15">
              <path fill="currentColor" fill-rule="evenodd"
                d="M11.782 4.032a.575.575 0 1 0-.813-.814L7.5 6.687L4.032 3.218a.575.575 0 0 0-.814.814L6.687 7.5l-3.469 3.468a.575.575 0 0 0 .814.814L7.5 8.313l3.469 3.469a.575.575 0 0 0 .813-.814L8.313 7.5z"
                clip-rule="evenodd" />
            </svg>
          </button>
        </div>
      </div>

    </div>


  </div>
</template>

<script lang="ts" setup>
import { computed, ref } from 'vue';

const data = ref({
  name: '',
  isChecked: false
})

const todos = ref([
  {
    id: 1,
    name: 'Todo 1',
    isChecked: false
  }
])

const totalTodos = computed(() => todos.value.length)

// Задача 3: Здесь надо что-то поменять
const completedTodos = computed(() => todos.value.length)
// Задача 3: Здесь надо что-то поменять

// Задача 1: Здесь надо что-то поменять
// Подсказка: Здесь мы просто пихаем херь дату, а надо пихать данные, которые ввел пользователь
const addNewTodo = () => {
  todos.value.push({ id: todos.value.length + 1, name: `Todo ${todos.value.length + 1}`, isChecked: false })
}
// Задача 1: Здесь надо что-то поменять

const removeTodoById = (id: number) => {
  todos.value = todos.value.filter((todo) => todo.id !== id)
}

</script>

