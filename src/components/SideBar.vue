<script setup>
    // Le composant peut emettre un évènement avec une seule option : selectOption
    const emits = defineEmits(['selectOption'])
    // Définition de la fonction selectOption avec la valeur isColor en argument
    const selectOption = (isColor) => {
        emits("selectOption", isColor)
    }
</script>

<template>
    <v-navigation-drawer expand-on-hover rail>

        <v-list>
            <!-- Image Avatar -->
            <v-list-item prepend-avatar="https://randomuser.me/api/portraits/women/85.jpg"
                subtitle="sandra_a88@gmailcom" title="Sandra Adams">
            </v-list-item>
        </v-list>

        <!-- Ligne de séparation-->
        <v-divider></v-divider>

        <v-list density="compact" nav>
            <!-- Icones -->
            <v-list-item prepend-icon="mdi-image" title="Color Gallary" value="color" @click="selectOption(true)">
            </v-list-item>
            <v-list-item prepend-icon="mdi-dialpad" title="Greyspace Gallary" value="grey" @click="selectOption(false)">
            </v-list-item>
            <v-list-item prepend-icon="mdi-folder" title="My Files" value="myfiles"></v-list-item>
            <v-list-item prepend-icon="mdi-account-multiple" title="Shared with me" value="shared"></v-list-item>
            <v-list-item prepend-icon="mdi-star" title="Starred" value="starred"></v-list-item>
        </v-list>

    </v-navigation-drawer>
</template>