<template>
  <v-app>

  <v-app-bar app
  clipped-right>
    <v-app-bar-nav-icon v-on:click="drawer=!drawer"></v-app-bar-nav-icon>
      <v-toolbar-title>Application</v-toolbar-title>
      <v-spacer></v-spacer>
      
      <v-app-bar-nav-icon v-on:click="drawerRight = !drawerRight"><v-icon>mdi-cog</v-icon></v-app-bar-nav-icon>
  </v-app-bar>
  

  <v-navigation-drawer app v-model="drawer" value="activeBtn">   
    <v-list> 
          <v-list-item to="/">
              <v-list-item-icon><v-icon>mdi-home-city</v-icon></v-list-item-icon>
              <v-list-item-content>Home</v-list-item-content>
          </v-list-item>
          <v-list-item to="/location">
              <v-list-item-icon><v-icon>mdi-map-marker</v-icon></v-list-item-icon>
              <v-list-item-content>Check-in</v-list-item-content>
          </v-list-item>
          <v-list-group>
          <template v-slot:activator>
            <v-list-item-icon><v-icon>mdi-message-text-outline</v-icon></v-list-item-icon>
            <v-list-item-content>Messages</v-list-item-content>
          </template>
            <v-list-item-content>
              <v-list>
                <v-list-item to="/message">
                  <v-avatar size="36px">
                    <img src="https://avatars0.githubusercontent.com/u/9064066?v=4&s=460" alt="">    
                  </v-avatar>
                  <v-list-item-title>John Leider</v-list-item-title>
                </v-list-item>
                <v-list-item>
                  <v-avatar size="36px">
                    <img src="https://cdn.vuetifyjs.com/images/lists/1.jpg" alt="">    
                  </v-avatar>
                  <v-list-item-title>John Wick</v-list-item-title>
                </v-list-item>
                <v-list-item>
                  <v-avatar size="36px">
                    <img src="https://cdn.vuetifyjs.com/images/lists/2.jpg" alt="">    
                  </v-avatar>
                  <v-list-item-title>Theo Walcot</v-list-item-title>
                </v-list-item>
              </v-list>
            </v-list-item-content>

          </v-list-group>


    </v-list>

    
  </v-navigation-drawer>

  <v-content>

    <v-container app fluid align-center style="padding:0">
      
    </v-container>
    <router-view>

    </router-view>
  </v-content>
  <v-navigation-drawer app
  v-model="drawerRight"
  clipped
  right>
  <v-list dense>
    <v-list-item>
      <v-switch
          v-model="$vuetify.theme.dark"
          hide-details
          insert
          label="Dark Mode">     
      </v-switch>
    </v-list-item>
  </v-list>
  </v-navigation-drawer>
</v-app>
</template>

<script>
  import Vue from 'vue'
  import Vuetify from 'vuetify/lib'
  new Vue({
    name:'#app',
    vuetify: new Vuetify()
  })
  export default{
      data () {
      return {
        drawer:null,
        drawerRight:null,
        activeBtn:1,
      }
    }
  }
</script>
<style lang="scss">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
a{
  text-decoration: none;

}
</style>