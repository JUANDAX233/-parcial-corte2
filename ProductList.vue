<template>
    <ion-list>
      <ion-card v-for="product in products" :key="product.id" class="product-card">
        <ion-card-header>
          <ion-card-title>{{ product.name }}</ion-card-title>
          <ion-card-subtitle>${{ product.price.toFixed(2) }}</ion-card-subtitle>
        </ion-card-header>
        <ion-card-content>
          <ion-button expand="block" color="success" @click="addToCart(product)">
            <ion-icon name="cart-outline" slot="start"></ion-icon>
            Agregar al carrito
          </ion-button>
        </ion-card-content>
      </ion-card>
    </ion-list>
  </template>
  
  <script setup>
  import { ref } from 'vue';
  
  const products = ref([
    { id: 1, name: 'Producto A', price: 10 },
    { id: 2, name: 'Producto B', price: 20 },
  ]);
  
  const emit = defineEmits(['add-to-cart']);
  const addToCart = (product) => {
    emit('add-to-cart', product);
  };
  </script>
  
  <style scoped>
  .product-card {
    margin-bottom: 1rem;
  }
  </style>