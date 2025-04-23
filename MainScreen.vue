<template>
    <ion-page>
      <!-- Header mejorado -->
      <ion-header>
        <ion-toolbar color="primary">
          <ion-title class="ion-text-center">Pantalla Principal</ion-title>
        </ion-toolbar>
      </ion-header>
  
      <!-- Contenido principal -->
      <ion-content class="ion-padding">
        <ion-grid>
  
          <!-- Encabezado de factura -->
          <ion-row>
            <ion-col size="12">
              <invoice-header />
            </ion-col>
          </ion-row>
  
          <!-- Lista de productos -->
          <ion-row>
            <ion-col size-md="8" size-sm="12">
              <product-list @agregar-producto="agregarProducto" />
            </ion-col>
            <!-- Resumen parcial de productos -->
            <ion-col size-md="4" size-sm="12">
              <ion-card class="ion-padding">
                <ion-card-header>
                  <ion-card-title>Resumen Parcial</ion-card-title>
                </ion-card-header>
                <ion-card-content>
                  <ul>
                    <li v-for="(p, index) in productos" :key="index">
                      {{ p.nombre }} - ${{ p.precio }}
                    </li>
                  </ul>
                  <p><strong>Total Parcial:</strong> ${{ total }}</p>
                </ion-card-content>
              </ion-card>
            </ion-col>
          </ion-row>
  
          <!-- Selección de método de pago -->
          <ion-row>
            <ion-col size="12">
              <payment-selector v-model="selectedPayment" />
            </ion-col>
          </ion-row>
  
          <!-- Resumen de la venta -->
          <ion-row>
            <ion-col size="12">
              <ion-card class="ion-padding">
                <ion-card-header>
                  <ion-card-title>Resumen Final</ion-card-title>
                </ion-card-header>
                <ion-card-content>
                  <p><strong>Método de Pago:</strong> {{ selectedPayment }}</p>
                  <p><strong>Total:</strong> ${{ total }}</p>
                </ion-card-content>
              </ion-card>
            </ion-col>
          </ion-row>
  
        </ion-grid>
      </ion-content>
    </ion-page>
  </template>
  
  <script setup>
  import { ref, computed } from 'vue';
  
  // Importar componentes reutilizables
  import InvoiceHeader from '@/components/InvoiceHeader.vue';
  import ProductList from '@/components/ProductList.vue';
  import PaymentSelector from '@/components/PaymentSelector.vue';
  
  // Estado reactivo
  const productos = ref([]);
  const selectedPayment = ref('Efectivo');
  
  // Métodos
  function agregarProducto(producto) {
    productos.value.push(producto);
  }
  
  // Total calculado
  const total = computed(() => {
    return productos.value.reduce((suma, p) => suma + p.precio, 0);
  });
  </script>
  