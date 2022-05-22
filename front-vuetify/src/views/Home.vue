<template>
<div>
  <div>
  <Encabezado texto="Mis datos"/>
  </div>
  <v-container class="ma-2">
    <v-row justify="space-around">
      <v-card width="400">
        <v-img
          height="200px"
          src="https://64.media.tumblr.com/59b6f41945b28c257854324cde4b759f/0914f7b67e14e739-e5/s1280x1920/c0024256bd63c22da94c55656171ab1de28a6277.jpg"
        >
          <v-app-bar
            flat
            color="rgba(0, 0, 0, 0)"
          >

            <v-toolbar-title class="text-h6 white--text pl-0">
              ¿Quien soy?
            </v-toolbar-title>

            <v-spacer></v-spacer>

          </v-app-bar>

          <v-card-title class="white--text mt-8">
            <v-avatar size="56">
              <img
                alt="user"
                src="https://scontent.fcyw3-1.fna.fbcdn.net/v/t1.6435-9/98556959_1304285446434341_2476662757747851264_n.jpg?_nc_cat=111&ccb=1-5&_nc_sid=174925&_nc_eui2=AeGHvNlYxcx2sEHQi_dQWnaglyiSA7_S2EiXKJIDv9LYSH1G7WspdJgF5O2Li2JieUMBLeljLwe6BP9qXaffPI6k&_nc_ohc=dt2b2izntykAX_h8-Hz&_nc_ht=scontent.fcyw3-1.fna&oh=47f30fafa392a24674b3d78ca3f61bb5&oe=619CBFDE"
              >
            </v-avatar>
            <p class="ml-3">
              Evelyn De Leon Hernandez
            </p>
          </v-card-title>
        </v-img>

        <v-card-text>
          <div class="font-weight-bold ml-8 mb-2">
            Datos personales
          </div>

          <v-timeline
            align-top
            dense
          >
            <v-timeline-item
              v-for="message in messages"
              :key="message.time"
              :color="message.color"
              small
            >
              <div>
                <div class="font-weight-normal">
                  <strong>{{ message.from }}</strong> @{{ message.time }}
                </div>
                <div>{{ message.message }}</div>
              </div>
            </v-timeline-item>
          </v-timeline>
        </v-card-text>
      </v-card>
    </v-row>
  </v-container>
  </div>
</template>

<script>
import Encabezado from '@/components/Encabezado.vue'
  export default {
    name: 'Home',
    components: {
      Encabezado
    },
    data: () => ({
      messages: [
        {
          from: 'Escuela',
          message: `Universidad Tecnologica de Salamanca`,
          time: '10:42am',
          color: 'deep-purple lighten-1',
        },
        {
          from: 'Carrera',
          message: 'Tecnologias de la Informacion, Area Desarrollo de Software Multiplataforma',
          time: '10:37am',
          color: 'green',
        },
        {
          from: 'Grado y Grupo',
          message: '4 A',
          time: '9:47am',
          color: 'deep-purple lighten-1',
        },
      ],
    }),
  }
</script>
