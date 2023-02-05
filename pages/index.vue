<template>
  <div>
    <h1>俺はジャイアン</h1>
    <p>ガキ大将</p>
    <div>Count:{{ count }}</div>
    <h2>{{ $hello('Wooooooorld') }}</h2>
    <p>
      hahahaha {{resData['data'][0]['title']}}
    </p>
    <div>
      <button @click="() => inc()">increase</button>
      <button @click="() => dec()">decrease</button>
    </div>
  </div>
  <div>
    <img src="~/assets/icon.webp" alt="Nuxt3 Icon" />
  </div>
  <div>
    <img src="/icon.jpeg" alt="Nuxt3 Icon" />
    <img src="/sample.avif" />
  </div>
</template>

<script setup>
definePageMeta({
  layout: 'default',
});
const { count, inc, dec } = useCounter(100);
const { $hello } = useNuxtApp();


const url = "http://localhost:8080/api/v1/posts"

const headers = new Headers({
  Authorization: `...`,
});
const res = await fetch(url, {
  method: "GET",
  headers: headers,
});
const resData = await res.json();
console.log(`** ${res.status}`, resData);
</script>
