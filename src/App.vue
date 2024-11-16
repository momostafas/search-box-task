<script setup lang="ts">
import { RouterLink, RouterView } from 'vue-router'
import HelloWorld from './components/HelloWorld.vue'
import Search from '@/components/Search.vue'

const articles = [
  {
    title: 'Article 1',
    body: 'lorem article 1 lkdmsalkdmsalkmd dnskad mn dkjandk mn kdj askjd asd'
  },
  {
    title: 'Article 2',
    body: 'lorem article 4 lkdmsalkdmsalkmd dnskad mn dkjandk mn kdj askjd asd'
  },
  {
    title: 'Article 3',
    body: 'lorem ipsum 3 lkdmsalkdmsalkmd dnskad mn dkjandk mn kdj askjd asd'
  },
]
</script>

<template>
  <Search :articles="articles" />
</template>

<style scoped>
</style>
