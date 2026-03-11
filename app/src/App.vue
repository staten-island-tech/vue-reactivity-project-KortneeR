<template>
  <div class="app-container">
    
    <h1 class="title">Ice Cream Builder</h1>

    <div class="sidebar">
      <h2>Selected Items</h2>
      <div v-if="selectedItems.length === 0">No items added</div>
      <ul>
        <li v-for="item in selectedItems" :key="item.id">
          {{ item.name }} - ${{ item.price }}
        </li>
      </ul>
    </div>

    <div class="main">
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

import {ref} from "vue"

const items = ref([
    {
        id: 1,
        name: "Waffle Cone",
        price: 1.99,
        image: "waffle-cone.png",
        category: "base",
    },
    {
        id: 2,
        name: "Cup",
        price: 0.99,
        image: "icecream-cup.png",
        category: "base",
    },
    {
        id: 3,
        name: "Vanilla Ice Cream",
        price: 3.99,
        image: "vanilla-cream.png",
        category: "icecream",
    },
    {
        id: 4,
        name: "Chocolate Ice Cream",
        price: 3.99,
        image: "chocolate-cream.png",
        category: "icecream",
    },
    {
        id: 5,
        name: "Strawberry Ice Cream",
        price: 3.99,
        image: "strawberry-cream.png",
        category: "icecream",
    },
    {
        id: 6,
        name: "Caramel Syrup",
        price: 0.50,
        image: "caramel-syrup.png",
        category: "topping",
    },
    {
        id: 7,
        name: "Chocolate Syrup",
        price: 0.50,
        image: "chocolate-syrup.png",
        category: "topping",
    },
    {
        id: 8,
        name: "Strawberry Syrup",
        price: 0.50,
        image: "strawberry-syrup.png",
        category: "topping",
    },
    {
        id: 9,
        name: "Rainbow Sprinkles",
        price: 0.50,
        image: "rainbow-sprinkles.png",
        category: "topping",
    },
    {
        id: 10,
        name: "Chocolate Sprinkles",
        price: 0.50,
        image: "chocolate-sprinkles.png",
        category: "topping",
    },
    {
        id: 11,
        name: "Cherry",
        price: 0.50,
        image: "cherry.png",
        category: "topping",
    }
])

const selectedItems = ref([])

// Add item to sidebar if not already added
function addItem(item) {
  if (!selectedItems.value.includes(item)) {
    selectedItems.value.push(item)
  }
}
</script>

<style>

.title {
  font-size: 40px;
  margin-bottom: 30px;
  text-align: center; 
  width: 100%;
}

.menu {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 20px;
  padding: 20px;
}

.card {
  background: white;
  border-radius: 12px;
  padding: 15px;
  text-align: center;
  box-shadow: 0px 5px 12px rgba(0,0,0,0.1);
}

.card-image {
  width: 120px;
}

.price {
  font-weight: bold;
}

</style>

