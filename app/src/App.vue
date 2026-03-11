<template>
  <div class="app-container">
    
    <h1 class="title">Ice Cream Builder</h1>

    <div class="sidebar">
      <h2>Ice Cream Builder</h2>
      <div v-if="selectedItems.length === 0">No items added</div>

      <div class="ice-cream-stack">
        <img
          v-for="item in selectedItems"
          :key="item.id"
          :src="item.image"
          class="stacked-image"
        />
      </div>

      <div v-if="selectedItems.length > 0" class="total-price">
        Total: ${{ totalPrice }}
      </div>
    </div>

    <div class="cards-container">
      <div class="menu">
        <div v-for="item in items" :key="item.id" class="card">
          <img :src="item.image" class="card-image">
          <h3>{{ item.name }}</h3>
          <p>${{ item.price }}</p>
          <button @click="addItem(item)">Add</button>
        </div>
      </div>
    </div>

  </div>
</template>

<script setup>
import { ref, computed } from "vue"

const items = ref([
    { id: 1, name: "Waffle Cone", price: 1.99, image: "waffle-cone.png", category: "base" },
    { id: 2, name: "Cup", price: 0.99, image: "icecream-cup.png", category: "base" },
    { id: 3, name: "Vanilla Ice Cream", price: 3.99, image: "vanilla-cream.png", category: "icecream" },
    { id: 4, name: "Chocolate Ice Cream", price: 3.99, image: "chocolate-cream.png", category: "icecream" },
    { id: 5, name: "Strawberry Ice Cream", price: 3.99, image: "strawberry-cream.png", category: "icecream" },
    { id: 6, name: "Caramel Syrup", price: 0.50, image: "caramel-syrup.png", category: "topping" },
    { id: 7, name: "Chocolate Syrup", price: 0.50, image: "chocolate-syrup.png", category: "topping" },
    { id: 8, name: "Strawberry Syrup", price: 0.50, image: "strawberry-syrup.png", category: "topping" },
    { id: 9, name: "Rainbow Sprinkles", price: 0.50, image: "rainbow-sprinkles.png", category: "topping" },
    { id: 10, name: "Chocolate Sprinkles", price: 0.50, image: "chocolate-sprinkles.png", category: "topping" },
    { id: 11, name: "Cherry", price: 0.50, image: "cherry.png", category: "topping" }
])

const selectedItems = ref([])

function addItem(item) {
  if (!selectedItems.value.includes(item)) {
    selectedItems.value.push(item)
  }
}

const totalPrice = computed(() => {
  return selectedItems.value.reduce((sum, item) => sum + item.price, 0).toFixed(2)
})
</script>

<style>

.title {
  font-size: 40px;
  margin-bottom: 30px;
  text-align: center; 
  width: 100%;
}

.sidebar {
  width: 250px;             
  background: #f8f8f8;
  padding: 20px;
  border-radius: 12px;
  box-shadow: 0 4px 10px rgba(0,0,0,0.1);
  height: fit-content;
}

.ice-cream-stack {
  display: flex;
  flex-direction: column-reverse; 
  align-items: center;
  margin-top: 10px;
}

.stacked-image {
  width: 80px;
  margin-top: -20px; 
}

.total-price {
  margin-top: 20px;
  font-weight: bold;
  font-size: 18px;
  text-align: center;
}

.cards-container {
  flex: 1;                 
}

.menu {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(150px, 1fr));
  gap: 20px;
}

.card {
  background: rgb(250, 190, 240);
  border-radius: 12px;
  padding: 15px;
  text-align: center;
  box-shadow: 0 4px 10px rgba(0,0,0,0.1);
}

.card-image {
  width: 100px;
  margin-bottom: 10px;
}

.button {
  margin-top: 10px;
  padding: 5px 10px;
}

</style>