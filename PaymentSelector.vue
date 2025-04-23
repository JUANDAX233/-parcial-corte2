<template>
    <ion-card>
      <ion-card-header>
        <ion-card-title>Selecciona un Método de Pago</ion-card-title>
      </ion-card-header>
      <ion-card-content>
        <ion-list>
          <ion-radio-group
            v-model="paymentMethod"
            @ionChange="emit('select-payment', paymentMethod)"
          >
            <ion-item>
              <ion-radio slot="start" value="efectivo"></ion-radio>
              <ion-label>Efectivo</ion-label>
            </ion-item>
            <ion-item>
              <ion-radio slot="start" value="tarjeta"></ion-radio>
              <ion-label>Tarjeta</ion-label>
            </ion-item>
          </ion-radio-group>
        </ion-list>
      </ion-card-content>
    </ion-card>
  </template>
  
  <script setup>
  import { ref } from 'vue';
  
  // Estado reactivo para el método de pago
  const paymentMethod = ref('efectivo');
  
  // Evento emitido al seleccionar el método de pago
  const emit = defineEmits(['select-payment']);
  </script>
  
  <style scoped>
  /* Espaciado entre los ítems para mejor legibilidad */
  ion-item {
    margin-bottom: 10px;
  }
  </style>