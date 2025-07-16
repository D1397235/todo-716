<!--使用todoitem.vue元件-->
<!--label 使用範圍值 done 預設選取-->
<!--data 新增 todoitems 資料 裡面幫我新增四筆代辦事項-->
<!--使用 ToDoItem 元件，並且使用 v-for 迴圈來顯示 todoItems todoitem-->
<!--引入todoform元件-->


<template>
  <div class="app">
    <h1>待辦事項清單</h1>
    <ToDoForm @add-todo="addTodo" />
    <div class="todo-list">
      <ToDoItem
        v-for="(item, index) in todoItems"
        :key="index"
        :label="item.label"
        :done="item.done"
      />
    </div>
  </div>
</template>

<script>
import ToDoItem from './components/ToDoItem.vue';
import ToDoForm from './components/ToDoForm.vue';
import { ref } from 'vue';
export default {
  name: 'App',
  components: {
    ToDoItem,
    ToDoForm
  },
  setup() {
    const todoItems = ref([
      { label: '買菜', done: false },
      { label: '運動', done: true },
      { label: '讀書', done: false },
      { label: '寫程式', done: true }
    ]);

    const addTodo = (newTodo) => {
      todoItems.value.push({ label: newTodo, done: false });
    };

    return {
      todoItems,
      addTodo
    };
  }
};
</script>
