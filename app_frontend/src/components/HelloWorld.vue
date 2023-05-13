<template>
  <v-container>
      <v-col cols="12">
        <v-img
          :src="require('../assets/stonkify.png')"
          class="my-3"
          contain
          height="200"
        />
        <h1 class="display-2 font-weight-bold mb-3" justify="center">
          STONKIFY
        </h1>
      </v-col>
      <v-row justify="center">
      <v-col class="mb-4" v-for="product in productList" :key="product.id" :product="product" >
        
          <!-- <div v-for="product in productList" :key="product.id" :product="product">
          {{ product.url_img}}
          </div> -->
        
          <v-card class="mx-auto" max-width="344" >

          <v-img 
          :src= "product.url_img"
          height="200px"
          cover
          ></v-img>

          <v-card-title>
          {{ product.name }}
          </v-card-title>

          <v-card-actions>
          <v-btn
            v-on:click="this.$router.push({ name: Product, params: { id: product.id } })"
          >
            View
          </v-btn>

          <v-spacer></v-spacer>
          </v-card-actions>
          </v-card>
        </v-col>
      </v-row>
  </v-container>
</template>

<script>
  export default {
    name: 'HelloWorld',

    data(){
      return {
        productList: []
      }
    },
    created(){
      fetch("https://localhost:7063/Stock")
            .then(res => res.json())
            .then(data => 
              this.productList = data
            )
    },
    methods: {
    
      }
    
  }
</script>







