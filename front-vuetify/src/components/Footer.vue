<template>
    <v-footer dark height="auto">
      <v-card flat tile class="#3E3E3E  white--text text-xs-center flex">
        <v-card-text>
          <v-btn v-for="icon in icons" :key="icon" class="mx-3" dark icon>
            <v-icon size="24px">
                {{icon}}
            </v-icon>
          </v-btn>
        </v-card-text>
      <v-card-text class="text-center">
          Todos los derechos reservados© Evelyn De Leon Hernandez 
        <v-spacer></v-spacer>
          Universidad Tecnologica de Salamanca
        <v-spacer></v-spacer>
          Tecnologias de la Informacion, Area Desarrollo de Software Multiplataforma
        <v-spacer></v-spacer>
          4 "A"

      </v-card-text>

      <v-divider></v-divider>

      <v-card-text class="white--text text-center">
        {{ new Date().getFullYear() }} — <strong>UTS</strong>
      </v-card-text>
    </v-card>
  </v-footer>
</template>

<script>
  export default {
    data: () => ({
      icons: [
        'mdi-facebook',
        'mdi-twitter',
        'mdi-instagram',
      ],
      link:[

      ]
    }),
  }
</script>