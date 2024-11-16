<template>
  <div class="search-container">
    <h1>Search</h1>
    <input
      v-model="searchValue"
      placeholder="Search articles..."
      @input="filterArticles"
    />
    <p>{{ filteredArticles.length }} posts were found.</p>

    <div v-for="(article, index) in filteredArticles" :key="index" class="article">
      <h3 v-html="highlightText(article.title)"></h3>
      <p v-html="highlightText(article.body)"></p>
    </div>
  </div>
</template>

<script setup>
import { ref, computed } from "vue";

  const props = defineProps( {
    articles: {
      type: Array,
      required: true,
    },
  })

    const searchValue = ref("");

    const filteredArticles = computed(() => {
      return props.articles.filter(
        (article) =>
          article.title.toLowerCase().includes(searchValue.value.toLowerCase()) ||
          article.body.toLowerCase().includes(searchValue.value.toLowerCase())
      );
    });

    const highlightText = (text) => {
      const regex = new RegExp(`(${searchValue.value})`, "gi");
      return searchValue.value ? text.replace(regex, "<mark>$1</mark>") : text;
    };
</script>

<style>
mark {
  background-color: yellow;
}

.search-container {
  margin: 0 auto;
  width: 100%;
  padding: 20px;
  display: block;
}
input {
  padding: 10px;
  width: 400px;
  margin-bottom: 10px;
  border: 1px solid #ccc;
  border-radius: 5px;
}

.article {
  border-bottom: 1px solid #ccc;
  padding: 10px 0;
}
</style>
