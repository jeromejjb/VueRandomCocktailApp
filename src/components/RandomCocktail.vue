<template>
    <div>
      <h2>{{ cocktail.strDrink }}</h2>
      <img :src="cocktail.strDrinkThumb" alt="Cocktail Image" />
      <h3>Ingredients:</h3>
      <ul>
        <li v-for="(value, key) in ingredients" :key="key">{{ value }}</li>
      </ul>

      <button class="btn" @click="fetchRandomCocktail">Get Random Cocktail</button>

    
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        cocktail: {},
        ingredients: [],
      };
    },
    created() {
      fetch("https://www.thecocktaildb.com/api/json/v1/1/random.php")
        .then((response) => response.json())
        .then((data) => {
          this.cocktail = data.drinks[0];
          for (let i = 1; i <= 15; i++) {
            const ingredient = this.cocktail[`strIngredient${i}`];
            const measure = this.cocktail[`strMeasure${i}`];
            if (ingredient) {
              this.ingredients.push(`${measure} ${ingredient}`);
            }
          }
        });
    },
    methods: {
  fetchRandomCocktail() {
    this.ingredients = [];
    fetch("https://www.thecocktaildb.com/api/json/v1/1/random.php")
      .then((response) => response.json())
      .then((data) => {
        this.cocktail = data.drinks[0];
        for (let i = 1; i <= 15; i++) {
          const ingredient = this.cocktail[`strIngredient${i}`];
          const measure = this.cocktail[`strMeasure${i}`];
          if (ingredient) {
            this.ingredients.push(`${measure} ${ingredient}`);
          }
        }
      });
  },
},

  };
  </script>
  
  <style scoped>
.container {
  max-width: 500px;
  margin: 0 auto;
  text-align: center;
}

h2 {
  font-size: 2rem;
  margin-top: 1.5rem;
  padding-left: 67%;
}

.image-container {
  margin: 1.5rem 0;
}

img {
  max-width: 100%;

}

h3 {
  font-size: 1.5rem;
  margin-top: 1.5rem;
  padding-left: 55%;
}

ul {
  list-style: none;
  padding: 0;
  margin: 0;
}

li {
  margin-bottom: 0.5rem;
  padding-left: 55%;
}

.btn {
  background-color: #2e6b9e;
  border: none;
  color: white;
  padding: 1rem 2rem;
  font-size: 1rem;
  margin-top: 2rem;
  cursor: pointer;
  border-radius: 5px;
  transition: background-color 0.3s ease;
}
.btn{
    margin-left: 55%;

}

.btn:hover {
  background-color: #1f4c75;
}
</style>