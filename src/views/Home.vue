<template>
  <div class="home">
    <convertidor></convertidor>
    
  </div>
</template>

<script>
// @ is an alias to /src
import Convertidor from '@/components/Convertidor.vue'

export default {
  name: 'home',
  components: {
    Convertidor
  }
}
</script>
