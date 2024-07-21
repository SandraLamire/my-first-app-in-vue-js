<script setup>
    const p = defineProps(["isWithColor"]);
    const copyURL = async (url) => {
        await navigator.clipboard.writeText(url)
    }
</script>

<template>
    <!-- Ajout d'une marge grâce à une classe intégrée : https://vuetifyjs.com/en/styles/spacing/ -->
    <v-card class="mx-5 my-2 pa-3">
        <v-row>
            <!-- Chaque colonne prend 6 places sur une grille de 12 -->
            <!-- sm, md, lg pour Responsive (small, medium, large) -->
            <v-col v-for="n in 200" cols="6" sm="4" md="2" lg="1">
                <v-hover v-slot="{ isHovering, props }">
                    <!-- @click = Au clic sur une carte, copier l'url dans le presse papier -->
                    <v-card :elevation="isHovering ? 12 : 2" v-blid="props"
                        @click="copyURL(`https://picsum.photos/500/300?image=${n * 5 + 10}${p.isWithColor ? '' : '&grayscale'}`)">
                        <!-- lazy-src : effet d'images floues avant le défilement jusqu'en bas de page -->
                        <v-img
                            :src="`https://picsum.photos/500/300?image=${n * 5 + 10}${p.isWithColor ? '' : '&grayscale'}`"
                            :lazy-src="`https://picsum.photos/10/6?image=${n * 5 + 10}${p.isWithColor ? '' : '&grayscale'}`"
                            aspect-ratio="1" cover>
                            <template v-slot:placeholder>
                                <v-row class="fill-height ma-0" align="center" justify="center">
                                    <!-- Rond de chargement des images -->
                                    <v-progress-circular color="grey-lighten-5" indeterminate></v-progress-circular>
                                </v-row>
                            </template>
                        </v-img>
                    </v-card>
                </v-hover>
            </v-col>
        </v-row>
    </v-card>
</template>