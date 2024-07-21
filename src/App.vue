<script setup>
  import SideBar from "./components/SideBar.vue"
  import ImageGallary from "./components/ImageGallary.vue"
  import { ref } from "vue"

  // Ajout d'une constante pour choix couleur/gris pour affichage photos
  const isWithColor = ref(true)

  const onSelectOption = (isColor) => {
    isWithColor.value = isColor
  }
</script>

<template>
  <v-app>
    <!-- Accès aux routes définies dans script setup -->
    <router-view />

    <!-- SIDEBAR COMPONENT avec utilisation de l'évènement enfant-->
    <SideBar @selectOption="onSelectOption" />
    <v-main>
      <!-- CARDS COMPONENT avec la couleur comme "accessoire" -->
      <ImageGallary :isWithColor="isWithColor" />
    </v-main>
  </v-app>
</template>