<template>
    <v-layout :wrap="true">
        <v-flex xs12>
            <v-card>
                <v-date-picker 
                v-model="fecha"
                full-width
                locale="es-cl"
                :min="minimo"
                :max="maximo"
                ></v-date-picker>
            </v-card>
            <v-card color="error" dark>
                <v-card-text class="display-1">
                    650 - {{ fecha }}
                </v-card-text>
            </v-card>
        </v-flex>
    </v-layout>
</template>

<script>
import axios from 'axios';

export default{

     mounted(){
        this.getDolar();
    },
    data(){
        return{
            fecha: '',
            minimo: '1984',
            maximo: new Date().toISOString().substr(0,10)
            }
    },
    methods:{
        async getDolar(){
            let data = await axios.get('https://mindicador.cl/api/dolar/' )
            console.log(data)
        
    }
    }
   

}
</script>