<template>
  <v-card>
    <v-navigation-drawer
      v-model="drawer"
      :mini-variant.sync="mini"
      permanent
      app
      dark   
    >
      <v-list-item class="px-2 ">
        <v-list-item-avatar>
          <v-img src="https://scontent.fcyw3-1.fna.fbcdn.net/v/t39.30808-6/242522983_1672944856235063_5769246857013198551_n.jpg?_nc_cat=109&ccb=1-5&_nc_sid=09cbfe&_nc_eui2=AeF3GY7LwL5KW4QuF0Hjo_ctOPlVF5Og54c4-VUXk6DnhzdKfnXTRmtOvuhG0P3hBur40ByPdyAa5SmgKhMYUn1Y&_nc_ohc=5HnMQgJy1sUAX_imGDZ&_nc_oc=AQmbYPmlgpWWbqlDyl0CiYpEC7UY8qNq9AnP1wYmiTSGxbSASm0LJy2lP7xoVovmPL0&_nc_ht=scontent.fcyw3-1.fna&oh=c91d143a983f44313cdcdd05bbbac82b&oe=6181BE01"></v-img>
        </v-list-item-avatar>

        <v-list-item-title>Eve De Leon</v-list-item-title>

        <v-btn
          icon
          @click.stop="mini = !mini"
        >
          <v-icon>mdi-chevron-left</v-icon>
        </v-btn>
      </v-list-item>

      <v-divider></v-divider>

      <v-list dense>
        <v-list-item
          v-for="item in items"
          :key="item.title"
          link
        >
          <v-list-item-icon>
            <v-icon>{{ item.icon }}</v-icon>
          </v-list-item-icon>

          <v-list-item-content>
            <router-link class="link" :to="`${ item.path }`"> 
              {{ item.title }}
              </router-link>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>
  </v-card>

</template>

<script>
  export default {
    data () {
      return {
        drawer: true,
        items: [
          { title: 'Datos personales', icon: 'mdi-account-circle-outline', path: '/' },
          { title: 'Usuarios', icon: 'mdi-account-group', path: '/listar' },
          { title: 'Crear Usuario', icon: 'mdi-account-plus-outline', path: '/crear' }
        ],
        mini: true,
      }
    },
  }
</script>

<style scoped>
.link{
  text-decoration:none;
  color: rgb(192, 214, 203);
}
</style>