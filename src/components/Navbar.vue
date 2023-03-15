<script setup>
  import gitHubIcon from './icons/gitHubIcon.vue';
</script>

<template>

  <nav>
    <div class="navbar">
      <gitHubIcon class="github-icon"/>
      <h1>Maame's GitHub.</h1>
    </div>
  </nav>

</template>

<style scoped>

.navbar {
  display: flex;
  align-items: center;
  gap: 10px;
  justify-content: center;
  background-color: #00bd7e;
  /* background-color: #1B9AAA; */
  text-align: center;
  padding: 20px;
  margin-bottom: 100px
}

.github-icon {
  font-size: 3rem;
}
</style>
