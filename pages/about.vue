<template>
    <div>
        <h1>About Us</h1>
        <p>This is me.</p>
    </div>
    <div>
        <button @click="enableCustomLayout">Update layout</button>
    </div>
</template>

<script setup>
function enableCustomLayout() {
  setPageLayout('custom');
}
definePageMeta({
  layout: 'default',
});
useHead({
  title: 'Aboutページ',
  meta: [
    {
      name: 'description',
      content: 'Aboutページ',
    },
  ],
});
</script>