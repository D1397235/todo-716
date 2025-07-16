<script>
// 當按下新增按鈕時 會觸發onSubmit方法
// data 會有lable 屬性用來儲存代辦事項
import { ref } from 'vue';
export default {
  name: 'ToDoForm',
  emits: ['add-todo'],
  setup(props, { emit }) {
    const label = ref('');

    const submitTodo = () => {
      if (label.value.trim() !== '') {
        emit('add-todo', label.value);
        label.value = ''; // 清空輸入框
      }
    };

    return {
      label,
      submitTodo
    };
  }
};
</script>

<template>
<!--  一個輸入表單用來新增代辦事項-->
<!--  label 提示要輸入什麼-->
<!--  input 是文字輸入匡 會有 id name 屬性-->
<!--  按鈕用來新增代辦事項-->
<!--  輸入的內容要跟 data 的 label 做雙向綁定-->
  <form @submit.prevent="submitTodo">
    <label for="todo-input">新增代辦事項:</label>
    <input
      type="text"
      id="todo-input"
      v-model="label"
      name="todo-input"
      required
    />
    <button type="submit">新增</button>
  </form>
</template>

<style scoped>

</style>