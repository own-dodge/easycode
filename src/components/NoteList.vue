<template>
  <ul class="note-list">
    <NoteItem @remove="$emit('remove', note)" :note="note" v-for="note in noteList" :key="note.id" />
    <h2 v-if="noteList.length == 0">Нет заметок</h2>
  </ul>
</template>

<script>
import NoteItem from '@/components/NoteItem.vue';

export default {
  components: { NoteItem },
  props: ['noteList']
}
</script>

<style scoped>
.note-list {
  width: 50%;
}
</style>