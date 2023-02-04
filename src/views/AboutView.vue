<template>
  <div class="about">
    <catalogo />
    <barra_nav />
  </div>
</template>
<script>
import catalogo from '@/components/catalogo.vue'
import barra_nav from '@/components/barra_nav.vue'

export default {
  name: 'HomeView',
  components: {
    catalogo,barra_nav

  }
}
</script>

