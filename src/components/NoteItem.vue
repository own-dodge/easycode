<template class="note-item">
  <li class="note-item">
    <div>
      <h2 class="note-title">{{ note.title }}</h2>
      <ul class="todo-list">
        <li v-for="todo in note.todoList" class="todo-item" :key="todo.id">
          <label class="custom-checkbox">
            <input type="checkbox" name="" id="" disabled>
            <span class="checkbox-label">{{ todo.title }}</span>
          </label>
        </li>
      </ul>
    </div>
    <div class="note-btns">
      <ButtonUI @click="$emit('remove', note)">Удалить</ButtonUI>
    </div>
  </li>
</template>

<script>

export default {
  props: ['note'],
}
</script>

<style scoped>
.note-item {
  padding: 15px;
  border: 2px solid blue;
  display: flex;
  align-items: center;
  justify-content: space-between;
}

.note-item:not(:last-child) {
  margin-bottom: 15px;
}

input[type="checkbox"] {
  display: none;
}
.custom-checkbox {
  display: flex;
  align-items: center;
  margin-bottom: 10px;
}

.custom-checkbox::before {
  content: '';
  display: inline-block;
  width: 20px;
  height: 20px;
  border: 1px solid #000;
  background-color: #fff;
  pointer-events: none;
  flex-shrink: 0;
  margin-right: 5px;
}

.checkbox-label {
  font-size: 16px;
  color: #000;
  flex-grow: 1;
}
</style>