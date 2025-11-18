<script setup>
import { ref, onMounted } from 'vue';
import gsap from 'gsap';

onMounted(() => {
  gsap.fromTo(
    nav.value,
    { opacity: 0, y: 30 },
    { opacity: 1, y: 0, duration: 1, delay: 0.5, stagger: 0.5 }
  );
})

import logo from '/src/img/our-wedding-logo.svg';

const isOpen = ref(false);
const nav = ref(null);

const navigationItem = [
  {
    id: 1,
    name: 'Home',
    link: '/'
  },
  {
    id: 2,
    name: 'Venue',
    link: '/venue',
  },
  {
    id: 3,
    name: 'Day Guest',
    link: '/day-guest',
  },
  {
    id: 4,
    name: 'Evening Guest',
    link: '/evening-guest',
  },
  {
    id: 5,
    name: 'FAQ',
    link: '/faq',
  },
]

function handleMenu() {
  isOpen.value = !isOpen.value;
}
</script>

<template>
  <header class="max-w-content mx-auto mt-50 max-lg:mt-5">
    <nav ref="nav" class="opacity-0 translate-y-[30px] flex justify-between items-center *:flex w-full">
      <div class="flex-1">
        <img :src="logo" alt="Logo">
      </div>
      <div class="justify-center flex-2 max-lg:hidden">
        <ul class="flex gap-5">
          <li v-for="item in navigationItem" :key="item.id">
            <a :href="item.link">{{ item.name }}</a>
          </li>
        </ul>
      </div>
      <div class="flex-1 justify-end">
        <a href="/rsvp" class="bg-secondary-900 text-white py-3 px-5 shadow-md cursor-pointer max-lg:hidden">RSVP</a>
        <button @click="handleMenu()" class="bg-secondary-900 text-white py-3 px-5 shadow-md cursor-pointer hidden max-lg:block">{{ isOpen ? 'Close' : 'Menu' }}</button>
      </div>
    </nav>
  </header>
</template>

<style scoped></style>
