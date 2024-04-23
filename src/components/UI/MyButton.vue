<script>
  export default {
    name: 'my-button'
  }
</script>

<template>
  <button class="btn">
    <slot></slot>
  </button>
</template>

<style scoped>
.btn {
  padding: 10px 15px;
  background: none;
  color: #12cbd0;
  border: 1px solid #12cbd0;
  cursor: pointer;
}
</style>