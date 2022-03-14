<template>
  <div class="clickBlock" @click="endGame">block content</div>
</template>

<script>
export default {
  name: "MyBlock",
  methods: {
    endGame() {
      this.$emit("end");
    }
  }
}
</script>

<style scoped>

.clickBlock {
  width: 350px;
  height: 230px;
  margin: 30px auto;
  background: #4caf50;
  display: flex;
  justify-content: center;
  align-items: center;
  border-radius: 12px;
  font-weight: 600;
  cursor: pointer;
}

</style>
