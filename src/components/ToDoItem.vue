<!--Script會有輸入的參數Label，Label必填的，另外一個參數是done 是boolean-->
<!--Data包括 isDone 跟 props 的 done 一樣 ID前面有前綴字 ”todo-“ 加上UUID-->
<!--template會有DIV包括input跟Label input 是checkbox 裡面的屬性ID跟是否選取 要跟Data做雙向綁定-->
<!--Label 跟ID做雙向綁定 label 用輸入參數-->

<template>
  <div class="todo-item">
    <input
      type="checkbox"
      :id="id"
      v-model="isDone"
    />
    <label :for="id">{{ label }}</label>
  </div>
</template>

<script>
import { ref, computed } from 'vue';
import { v4 as uuidv4 } from 'uuid';
export default {
  name: 'ToDoItem',
  props: {
    label: {
      type: String,
      required: true
    },
    done: {
      type: Boolean,
      default: false
    }
  },
  setup(props) {
    const id = `todo-${uuidv4()}`;
    const isDone = ref(props.done);

    return {
      id,
      isDone,
      label: props.label
    };
  }
};
</script>
