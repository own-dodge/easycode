<template>
  <button>
    <slot></slot>
  </button>
</template>

<script>
export default {
  name: 'ButtonUI',
}
</script>

<style scoped>
button {
  padding: 10px 15px;
  background: none;
  color: blue;
  border: 1px solid blue;
  cursor: pointer;
  transition: background .3s ease-in-out, color .3s ease-in-out;
}

button:hover {
  background: blue;
  color: white;
}
</style>