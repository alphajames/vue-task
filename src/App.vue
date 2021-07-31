<template>
  <div class="row container-padding">
    <!-- HEADING CONTENT -->
    <div class="container-padding font-black col-xl-6 d-flex flex-column ps-5">
      <h1 class="font-poppins font-900 text-8xl mobile-3xl mt-5">
        <span><i class="fas fa-grip-lines-vertical font-orange"></i></span> Vue
        task.
      </h1>

      <p class="font-poppins font-300 text-2xl mobile-2xl">
        📍 Keep track of your task.
      </p>
      <div class="form-container">
        <form action="" @submit.prevent="addNewTodo">
          <input
            v-model="newTodo"
            type="text"
            class="font-poppins input-box form-control mb-3"
            placeholder="Enter your task here"
          />
          <p>
            <button class="font-poppins font-600 font-white submit">
              📌 Add Task
            </button>
          </p>
        </form>
      </div>
    </div>
    <!-- END HEADING CONTENT -->
    <!-- TASK CONTAINER -->
    <div class="col-xl-6 container-padding">
      <ul>
        <li v-for="(todo, index) in todos" :key="todo.id">
          <h1
            :class="{ done: todo.done }"
            @click="toggleDone(todo)"
            class="font-poppins text-2xl mobile-2xl pb-5"
          >
            <span class="border-orange ps-3">📋 {{ todo.content }}</span>

            <button class="ms-2 delete" @click="removeTask(todo)">
              <i class="far fa-trash-alt font-red"></i>
            </button>
          </h1>
        </li>
      </ul>
    </div>
    <!-- END TASK CONTAINER -->
  </div>
</template>

<script>
import { ref } from "vue";
export default {
  setup() {
    const newTodo = ref();
    const todos = ref([]);

    function addNewTodo() {
      todos.value.push({
        id: Date.now(),
        done: false,
        content: newTodo.value,
      });
      newTodo.value = "";
    }
    function toggleDone(todo) {
      todo.done = !todo.done;
    }
    function removeTask(index) {
      todos.value.splice(index, 1);
    }

    return {
      newTodo,
      addNewTodo,
      todos,
      toggleDone,
      removeTask,
    };
  },
};
</script>

<style>
input {
  width: 60% !important;
  height: 60px;
}
ul {
  list-style: none;
}
.submit {
  background-color: #18191b;
  border-color: #18191b;
  border-style: none;
  height: 50px;
  padding: 5px 15px 5px 15px;
  border-radius: 8px;
  outline: none;
}
.delete {
  background-color: transparent;

  border-style: none;
  padding: 3px 5px 3px 5px;
}
</style>
