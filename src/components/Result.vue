<template>
  <h3>Reaction time: {{ delay }}ms</h3>
  <h2 class="description">{{ description() }}</h2>
</template>

<script>
export default {
  name: "GameResult",
  props: ['delay'],
  methods: {
    description() {
      if (this.delay < 200) return "Rapid reaction";
      if (this.delay > 500) return "Super slow reaction";
      return "Normal reaction";
    }
  }
}
</script>

<style scoped>

.description {
  color: #00796b;
}

</style>
