<script setup> 
const model = defineModel({ type: String, default: '' }) 
</script> 
  
<template> 
  <form class="search" role="search" @submit.prevent> 
    <label for="q" class="sr-only">Rechercher un livre</label> 
    <input id="q" v-model="model" type="search" 
           placeholder="Titre, auteur…" /> 
  </form> 
</template> 

<style scoped>
.search__input { width: 100%; padding: var(--space-2) var(--space-4); border-radius: var(--radius); border: 1px solid #ccc; font-size: var(--fs-400); }
</style>
