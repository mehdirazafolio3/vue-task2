<script setup>
defineProps({
  name: {
    type: String,
    required: true
  },
  email: {
    type: String,
    required: true
  },
  age: {
    type: Number,
    required: true
  },
  birthYear: {
    type: Number,
    required: true
  }
})
</script>

<template>
 <div id="user-info">
            <h3>User Information</h3>
            <p><strong>Name:</strong> {{ name }}</p>
            <p><strong>Email:</strong> {{ email }}</p>
            <p><strong>Age:</strong> {{ age }}</p>
            <p><strong>Birth Year:</strong> {{ birthYear }}</p>

        </div>
</template>

<style scoped>

.user-info {
    background-color: #fff;
    padding: 20px;
    border-radius: 10px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.2);
    margin: 20px;
  }
</style>
