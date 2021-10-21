<template>
  <v-container>
    <v-row class="text-center">
      <v-col v-for="product in products" :key="product.id"  cols="4">

  <v-card
 
    :loading="loading"
    class="mx-auto my-12"
    max-width="354"
    elevation="10"
    
  >
    <template slot="progress">
      <v-progress-linear
        color="deep-purple"
        height="10"
        indeterminate
      ></v-progress-linear>
    </template>
 <div class="mydiv">
    <v-img
     class="myimg"
      :src="product.image"
    ></v-img></div>
    

    <v-card-title>{{product.title.substring(0, 30) + "..." }}</v-card-title>

    <v-card-text>
      <v-row
        align="center"
        class="mx-0"
      >
        <v-rating
          :value="4.5"
          color="amber"
          dense
          half-increments
          readonly
          size="14"
        ></v-rating>

        <div class="grey--text ms-4">
          4.5 (413)
        </div>
      </v-row>

      <div class="my-4 text-subtitle-1">
        $ • {{product.price}}
      </div>

      <div>{{product.category}}</div>
    </v-card-text>

    <v-divider class="mx-4"></v-divider>

    <!-- <v-card-title>Tonight's availability</v-card-title>

    <v-card-text>
      <v-chip-group
        v-model="selection"
        active-class="deep-purple accent-4 white--text"
        column
      >
        <v-chip>5:30PM</v-chip>

        <v-chip>7:30PM</v-chip>

        <v-chip>8:00PM</v-chip>

        <v-chip>9:00PM</v-chip>
      </v-chip-group>
    </v-card-text> -->

    <v-card-actions>
      <v-btn
        color="deep-purple lighten-2"
        text
        @click="reserve"
      >
        Reserve
      </v-btn>
    </v-card-actions>
  </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
import axios from 'axios'
  export default {
    name: 'HelloWorld',

    data: () => ({
products:[]
    }),
    created(){
      axios.get('https://61449702411c860017d25586.mockapi.io/Products')
      .then(res=>{
        console.log(res)
        this.products = res.data
      })
    }
  }
</script>
<style scoped>
.img {
  width: 100%;
  height: 250px;
}
.mydiv{  
  /* text-align: center; */
padding-left: 50px;

}
.myimg{
/* object-fit: scale-down; */
width: 220px;
height: 320px;
}
</style>