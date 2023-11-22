<template>
  <form @submit.prevent="createNote" class="form">
    <h3>Создание новой заметки</h3>
    <input v-focus v-model.trim="note.title" type="text" class="form-input" placeholder="Название заметки" required>
    <template v-for="todo in note.todoList" :key="todo.id">
      <input v-model.trim="todo.title" type="text" class="form-input" placeholder="Название задачи" required>
    </template>
    <ButtonUI class="form-btn">Создать заметку</ButtonUI>
  </form>
</template>

<script>
export default {
  data() {
    return {
      note: {
        title: '',
        todoList: [{ id: Date.now(), title: '' }],
      }
    }
  },
  methods: {
    createNote() {
      this.note.id = Date.now()
      this.$emit('create', this.note)
      this.note = {
        title: '',
        todoList: [{ id: null, title: '' }],
      }
    }
  }
}
</script>

<style scoped>
.form {
  display: flex;
  flex-direction: column;
}

.form-input {
  width: 100%;
  border: 2px solid blue;
  padding: 10px 15px;
  margin-bottom: 15px;
}

.form-btn {
  align-self: center;
}
</style>