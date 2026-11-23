<script setup> 
defineProps({ 
  book: { type: Object, required: true }, 
  favorite: { type: Boolean, default: false }, 
}) 
const emit = defineEmits(['toggle-favorite']) 
</script> 
  
<template> 
  <article class="book-card"> 
    <img class="book-card__cover" :src="book.cover" width="200" height="300" 
         :alt="'Couverture de ' + book.title" loading="lazy" /> 
    <div class="book-card__body"> 
      <h3 class="book-card__title">{{ book.title }}</h3> 
      <p class="book-card__author">{{ book.author }}</p> 
      <p class="book-card__status" 
         :class="{ 'book-card__status--off': !book.available }"> 
        {{ book.available ? 'Disponible' : 'Emprunté' }} 
      </p> 
      <button class="book-card__fav" type="button" 
              :aria-pressed="favorite" 
              @click="emit('toggle-favorite', book.id)"> 
        {{ favorite ? '★ Retirer des favoris' : '☆ Ajouter aux favoris' }} 
      </button> 
      <slot name="actions" /> 
    </div> 
  </article> 
</template> 
  
<style scoped>
.book-card { background: var(--color-surface); border-radius: var(--radius); overflow: hidden; box-shadow: 0 2px 8px rgba(0,0,0,0.1); display: flex; flex-direction: column; }
.book-card__cover { width: 100%; object-fit: cover; }
.book-card__body { padding: var(--space-4); flex-grow: 1; display: flex; flex-direction: column; }
.book-card__title { font-size: var(--fs-300); margin: 0 0 var(--space-2) 0; }
.book-card__author { margin: 0 0 var(--space-2) 0; color: #666; }
.book-card__status { font-weight: bold; color: var(--color-primary); margin-bottom: auto; }
.book-card__status--off { color: var(--color-danger); }
.book-card__fav { margin-top: var(--space-4); background: none; border: 1px solid #ccc; padding: 5px; border-radius: 5px; cursor: pointer; }
</style>