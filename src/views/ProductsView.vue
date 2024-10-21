<template>
  <Card />
  <router-link type="button" class="btn btn-primary back-to-home text-center mx-auto" to="/">
      Volver al Home
    </router-link>
</template>

<script>
// @ is an alias to /src
import Card from '../components/Card.vue'

export default {
  components: {
    Card
  }
}
</script>