<template>
  <div class="app">
    <header>
      <img alt="Vue logo" class="logo" src="./assets/logo.svg" width="125" height="125" />

      <div class="wrapper">
        <HelloWorld msg="Random Cocktail App" />
      </div>
    </header>

    <main>
      <RandomCocktail />
    </main>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'
import RandomCocktail from './components/RandomCocktail.vue'

export default {
  components: {
    HelloWorld,
    RandomCocktail
  }
}
</script>

<style scoped>
header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

h1 {
  margin-bottom: 1rem;
}

.wrapper {
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>
