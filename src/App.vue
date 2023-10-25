<!-- src/App.vue -->
<template>
  <ion-app>
    <ion-page>
      <ion-datetime-button datetime="datetime"></ion-datetime-button>

      <ion-modal :keep-contents-mounted="true">
        <ion-datetime id="datetime"></ion-datetime>
      </ion-modal>
      <to-do-list :todos="todos" @remove-todo="removeTodo" />
      <add-to-do @add-todo="addTodo" />
    </ion-page>
  </ion-app>
</template>

<script>
import { IonApp, IonDatetime, IonDatetimeButton, IonModal } from '@ionic/vue';
import ToDoList from './components/ToDoList.vue';
import AddToDo from './components/AddToDo.vue';
import { ref, defineComponent } from 'vue';
export default {
  components: {
    AddToDo,
    ToDoList,
    IonApp,
    IonDatetime,
    IonDatetimeButton,
    IonModal,
  },
  setup() {
    const todos = ref([]);
    const addTodo = (newTodo) => {
      todos.value.push(newTodo);
    };

    const removeTodo = (index) => {
      todos.value.splice(index, 1);
    };

    return {
      todos,
      addTodo,
      removeTodo,
    };
  },
};
</script>
