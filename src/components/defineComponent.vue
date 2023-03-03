import { defineComponent } from 'vue'

interface Cocktail {
  strDrink: string,
  strInstructions: string,
  strDrinkThumb: string,
  strIngredient1: string,
  strIngredient2: string,
  strIngredient3: string,
  strIngredient4: string,
  strIngredient5: string,
  strIngredient6: string,
  strIngredient7: string,
  strIngredient8: string,
  strIngredient9: string,
  strIngredient10: string,
  strIngredient11: string,
  strIngredient12: string,
  strIngredient13: string,
  strIngredient14: string,
  strIngredient15: string,
}

export default defineComponent({
  name: 'RandomCocktail',
  data() {
    return {
      cocktail: {} as Cocktail,
    }
  },
  methods: {
    async fetchCocktail() {
      const res = await fetch('https://www.thecocktaildb.com/api/json/v1/1/random.php')
      const { drinks } = await res.json()
      this.cocktail = drinks[0]
    }
  },
  mounted() {
    this.fetchCocktail()
  }
})
