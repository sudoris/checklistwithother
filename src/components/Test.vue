<template>
  <div>

    <div id='example-3'>
      <input type="checkbox" id="chili" value="Chili" v-model="ingredients">
      <label for="chili">Chili</label>
      <input type="checkbox" id="salt" value="Salt" v-model="ingredients">
      <label for="salt">Salt</label>
      <input type="checkbox" id="butter" value="Butter" v-model="ingredients">
      <label for="butter">Butter</label>
      <br>      
    </div>

    

    <div v-for="(item, index) in other" :key="index">
      <label for="ingredient">Ingredient:</label>
      <input type="text" id="ingredient" v-model="other[index]">
    </div>

    <div>
      <label for="ingredInput">Other: </label>
      <input type="text" id="ingredInput" v-model="myValue" @change="addIng">
    </div>



    
    <button @click="combine">Combine</button>
    
    <br>
    {{ myValue }}
    
    <br>
    <span>All ingredients: {{ ingredients }}</span>
    <br>

    <span>Other: {{ other }}</span>

    
    
    
  </div>
</template>

<script>
export default {
  name: "Test",
  data() {
    return {
      title: null,
      ingredients: [],
      other: [],
      myValue: null,
      feedback: null
    };
  },
  methods: {
    combine() {
      this.ingredients.push(...this.other)
    },
    // deletee() {
    //   // this.$delete(this.ingredients, 1)
    //   this.ingredients.splice(1, 1)
    // },    
    addIng(value){
      if (!this.ingredients.includes(this.myValue) && !this.other.includes(this.myValue)) {
        this.other.push(this.myValue)
      }
      
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1,
h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
