<template>
    <ion-header>
      <ion-toolbar color="primary">
        <ion-title class="ion-text-center">Detalles del Cliente</ion-title>
        <ion-buttons slot="end">
          <ion-button @click="guardarDatos">
            <ion-icon name="save-outline" slot="icon-only"></ion-icon>
          </ion-button>
        </ion-buttons>
      </ion-toolbar>
    </ion-header>
  
    <ion-content>
      <ion-list>
        <ion-item>
          <ion-label position="stacked">Nombre del cliente</ion-label>
          <ion-input v-model="customer.name" />
        </ion-item>
        <ion-item>
          <ion-label position="stacked">Dirección</ion-label>
          <ion-input v-model="customer.address" />
        </ion-item>
      </ion-list>
    </ion-content>
  </template>
  
  <script setup>
  import { reactive, watch } from 'vue';
  import { IonButtons, IonButton, IonIcon } from '@ionic/vue';
  
  const customer = reactive({ name: '', address: '' });
  const emit = defineEmits(['update-customer']);
  
  watch(customer, () => emit('update-customer', customer), { deep: true });
  
  function guardarDatos() {
    console.log('Datos guardados:', customer);
    // Agregar lógica para guardar los datos
  }
  </script>