<template>
  <div>
    <div>
      <Encabezado texto="Usuarios del sistema"/>
    </div>
    <div class="contenido">
    <div class="pa-4">
        <div>
            <v-data-table 
               :items-per-page="10" 
               :items="usuariosBD"
               :headers="headers"
               dark
               class="elevation 1"
            >
              <template #[`item.editar`]="{ item }">
                <v-btn color="indigo darken-1" fab small @click="editarUsuario(item.id)">
                  <v-icon color="indigo lighten-4">
                    mdi-account-edit
                  </v-icon>
                </v-btn>
              </template>
              <template #[`item.borrar`]="{ item }">
                <v-btn color="red darken-4" fab small @click="guardarUsuario(item.id)">
                  <v-icon color="indigo lighten-4">
                    mdi-trash-can
                  </v-icon>
                </v-btn>
              </template>
            </v-data-table>
            <v-dialog
              v-model="dialog"
              persistent
              max-width="500px"
            >
              <v-card>
                <v-card-title class="text-h5">
                  ¿Esta seguro de que quiere eliminar este usuario?  
                </v-card-title>
                <v-card-actions>
                  <v-spacer></v-spacer>
                  <v-btn
                    color="red darken-1"
                    text
                    @click="dialog = false"
                  >
                    Cancelar
                  </v-btn>
                  <v-btn
                    color="green darken-1"
                    text
                    @click="borrarUsuario(usuarioId)"
                  >
                    Eliminar
                  </v-btn>
                </v-card-actions>
              </v-card>
            </v-dialog>
        </div>
    </div>
    </div>
    </div>
</template>

<script>
import Encabezado from './Encabezado.vue'
export default {
    components:{
        Encabezado
    },
    data(){
        return{
        usuariosBD: [],
            headers: [
                {text: 'ID', value: 'id', align: 'center', sortable: false},
                {text: 'NOMBRE', value: 'nombre', align: 'center', sortable: false},
                {text: 'CORREO', value: 'correo', align: 'center', sortable: false},
                {text: 'EDITAR', value: 'editar', align: 'center', sortable: false},
                {text: 'BORRAR', value: 'borrar', align: 'center', sortable: false},
            ],
            itemsBD: [],
            dialog: false,
        }
    },
  created: function(){
        this.consultarUsuarios()
    },
    methods: {
        consultarUsuarios(){
            fetch('http://localhost/')
            .then(respuesta => respuesta.json())
            .then((datosRespuesta) => {
                this.usuariosBD = []
                if(typeof datosRespuesta[0].success === 'undefined'){
                    this.usuariosBD = datosRespuesta
                    this.usuariosBD.forEach( item => {
                        console.log(item)
                    })
                    //console.log(this.usuariosBD)
                }
            })
            .catch(console.log)
        },
        editarUsuario(id){
            this.$store.commit('setIdUsuario', id) //activa mutacion 
            window.location.href= "editar"
        },
        borrarUsuario(usuarioId){
            console.log(usuarioId)
            fetch('http://localhost/?borrar='+usuarioId)
            .then( respuesta => respuesta.json)
            .then( (datosRespuesta) => {
                this.usuarioId = null
                window.location.href = "listar"
            })
        },
        guardarUsuario(id){
            this.usuarioId = id                        
            this.dialog = true

        }
        
    }
}
</script>

<style scoped>
.contenido{
  min-height: calc(100vh - 80px - 70px);
}
</style>