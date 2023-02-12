<template>
  <h2>hahaha</h2>
  <p>test</p>
  <p>ユーザID: {{ router.params.id }}</p>
  <p>name: {{ data.data.name }}</p>
  <p>name: {{ data.data.classname }}</p>
  <p>name: {{ data.data.strength }}</p>
  <p>name: {{ data.data.skill }}</p>
  <p>name: {{ data.data.dexterity }}</p>
</template>

<script setup>
  const router = useRoute();

  const { data } = await useFetch('http://localhost:8080/api/v1/posts/' + router.params.id);
</script>
