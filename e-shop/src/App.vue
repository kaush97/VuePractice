<template>
  <v-app>
     <v-card
 v-if="isMobile"
    
  >
    <v-app-bar
      color="default"
      dark
      app
    >
      <v-app-bar-nav-icon @click="drawer = true"></v-app-bar-nav-icon>

      <v-toolbar-title>Title</v-toolbar-title>
    </v-app-bar>

  </v-card>
    <v-app-bar
    v-else
      app
      color=""
      dark
    >
      <div class="d-flex align-center">
        <v-img
          alt="Vuetify Logo"
          class="shrink mr-2"
          contain
          src="./assets/shopping-bag.png"
          transition="scale-transition"
          width="40"
        />
<span class="mt-3">E-Shop</span>
        <!-- <v-img
          alt="Vuetify Name"
          class="shrink mt-1 hidden-sm-and-down"
          contain
          min-width="100"
          src="https://cdn.vuetifyjs.com/images/logos/vuetify-name-dark.png"
          width="100"
        /> -->
      </div>
      <v-spacer></v-spacer>
       <nav class="navbar navbar-expand-lg fixed-top row">

                    <router-link tag="li" class="col" class-active="active" to="/" exact>Home</router-link>
                    <router-link tag="li" class="col" class-active="active" to="/CNN" exact>Today's Deal</router-link>
                    <router-link tag="li" class="col" class-active="active" to="/about" exact>Categories</router-link>
                    <router-link tag="li" class="col" class-active="active" to="/BBCSport" exact>Best Sellers</router-link>
                      <router-link tag="li" class="col" class-active="active" to="/BBCSport" exact>Contact</router-link>
        </nav>
      <!-- <ul><li>Home</li><li>Today's Deal</li><li>Category</li><li>Best Sellers</li><li>Contact</li></ul> -->
      <!-- <router-link>Home</router-link><router-link>Home</router-link><router-link>Home</router-link><router-link>Home</router-link> -->
 <v-btn
      @click="profile = !profile"
        target="_blank"
        text
      ><v-badge
          color="pink"
          content="0"
        >
        <v-icon>mdi-cart</v-icon>
        </v-badge>
      
      </v-btn>
      <v-btn
      v-if="login"
      @click="profile = !profile"
        target="_blank"
        text
      >
        
        <v-icon>mdi-account</v-icon>
      </v-btn>
        <v-btn
        href="https://github.com/vuetifyjs/vuetify/releases/latest"
        target="_blank"
        text
      >
      <span class="mr-2">Login/Sign Up</span></v-btn>
    
 <v-card
 style="position:absolute;right:0;top:60px"
       v-if="profile"
    class="mx-auto"
    max-width="400"
    tile
  >
     <v-list dense>
      <!-- <v-subheader>REPORTS</v-subheader> -->
      <v-list-item-group
        v-model="selectedItem"
        color="primary"
      >
        <v-list-item
          v-for="(item, i) in items"
          :key="i"
        >
          <v-list-item-icon>
            <v-icon v-text="item.icon"></v-icon>
          </v-list-item-icon>
          <v-list-item-content>
            <v-list-item-title v-text="item.text"></v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list-item-group>
    </v-list>

  </v-card>
    </v-app-bar>

    <v-main>
   
    <v-navigation-drawer
      v-model="drawer"
      absolute
      temporary
    >
      <v-list
        nav
        dense
      >
        <v-list-item-group
          v-model="group"
          active-class="deep-purple--text text--accent-4"
        >
          <v-list-item>
            <v-list-item-icon>
              <v-icon>mdi-home</v-icon>
            </v-list-item-icon>
            <v-list-item-title>Home</v-list-item-title>
          </v-list-item>

          <v-list-item>
            <v-list-item-icon>
              <v-icon>mdi-account</v-icon>
            </v-list-item-icon>
            <v-list-item-title>Account</v-list-item-title>
          </v-list-item>
        </v-list-item-group>
      </v-list>
    </v-navigation-drawer>
    <div style="margin-top:.1%">
   <v-carousel
    cycle
    height="300"
    hide-delimiter-background
    show-arrows-on-hover
  >
     <v-carousel-item
      v-for="(item,i) in slides"
      :key="i"
      :src="item.src"

    ></v-carousel-item>
  </v-carousel></div>
      <router-view/>
    </v-main>
  </v-app>
</template>

<script>
    var file1 = require('./assets/1.jpg')
    var file2 = require('./assets/2.jpg')
    var file3 = require('./assets/3.jpg')
    var file4 = require('./assets/4.jpg')
    var file5 = require('./assets/5.jpg')
    var file6 = require('./assets/6.jpg')

export default {
  name: 'App',

  data: () => ({
    //
     drawer: false,
      group: null,
      profile:false,
       selectedItem: 0,
      items: [
        { text: 'Profile', icon: 'mdi-account' },
        { text: 'Logout', icon: 'mdi-logout' }
      ],
        slides: [
          {
            src: file1,
          },
          {
            src: file2,
          },
          {
            src: file3,
          },
          {
            src: file4,
          },
            {
            src: file5,
          },
          {
            src: file6,
          },
        ],
  }),
  computed:{
    
isMobile() {
  return this.$vuetify.breakpoint.xsOnly;
}
  }
};
</script>
<style scoped>
li{
  display: inline;
  text-decoration: none;
  padding: 0px;
  
}
li:hover{
  color: orange;
}

nav li:hover,
 nav li.router-link-active,
 nav li.router-link-exact-active {
   /* background-color: indianred; */
  color: orange;
   cursor: pointer;
 }

</style>
