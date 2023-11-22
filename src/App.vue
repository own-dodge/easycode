<template>
  <div class="container">
    <h1 class="title">Список заметок</h1>
    <ButtonUI class="btn-create" @click="showDialog">Создать заметку</ButtonUI>
    <DialogUI v-model:show="dialogVisible">
      <NoteForm @create="createNote"/>
    </DialogUI>
    <NoteList @remove="removeNote" :noteList="noteList"/>
  </div>
</template>

<script>
import NoteForm from '@/components/NoteForm.vue';
import NoteList from '@/components/NoteList.vue';

export default {
  name: 'App',
  components: { NoteForm, NoteList },
  data() {
    return {
      noteList: [
        { id: 1, title: 'Дело 1', todoList: [{ id: 1, title: 'todo 1' }, { id: 2, title: 'todo 2' }] },
        { id: 2, title: 'Дело 2', todoList: [{ id: 1, title: 'todo 1' }, { id: 2, title: 'todo 2' }] }
      ],
      dialogVisible: false,
    }
  },
  methods: {
    createNote(note) {
      this.noteList.push(note)
      this.dialogVisible = false
    },
    removeNote(note) {
      const confirmDelete = confirm('Вы уверены?');
      if(confirmDelete) {
        this.noteList = this.noteList.filter((element) => element.id !== note.id)
      }
    },
    showDialog() {
      this.dialogVisible = true
    }
  }
}
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  list-style: none;
}

.container {
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 15px;
}

.title {
  margin-bottom: 20px;
}

.btn-create {
  margin-bottom: 30px;
}
</style>
