<script setup> 
defineProps({ 
  variant: { type: String, default: 'primary' }, // primary | ghost 
  to: { type: [String, Object], default: null },  // lien interne si renseigné 
}) 
</script> 
  
<template> 
  <component :is="to ? 'RouterLink' : 'button'" :to="to" :class="['btn', 'btn--' + variant]"> 
    <slot /> 
  </component> 
</template> 

<style scoped>
.btn {
  padding: var(--space-2) var(--space-4); border-radius: var(--radius);
  border: none; cursor: pointer; font-family: inherit; font-size: var(--fs-400);
  text-decoration: none; display: inline-block;
}
.btn--primary { background: var(--color-primary); color: var(--color-primary-contrast); }
.btn--ghost { background: transparent; color: var(--color-primary); border: 1px solid var(--color-primary); }
</style>