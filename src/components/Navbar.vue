<template>
  <nav>
    <v-app-bar color="#b91432" dark app>
      <v-app-bar-nav-icon @click.stop="drawer = !drawer"></v-app-bar-nav-icon>
      <v-toolbar-title class="text-uppercase ">
        <span id="sai">SAI-</span>
        <span id="sai">Board</span>
      </v-toolbar-title>
      <v-spacer></v-spacer>
      <v-menu offset-y>
        <template v-slot:activator="{ on }">
          <v-btn text v-on="on">
            <v-icon left>expand_more</v-icon>
            <v-avatar size="30">
              <img src="/img1.png" alt="" />
            </v-avatar>
          </v-btn>
        </template>
        <v-list flat>
          <!-- <v-list-item
            v-for="link in links"
            :key="link.text"
            router
            :to="link.route"
            active-class="border"
          > -->
          <v-list-item>
            <v-list-item-title>Profile</v-list-item-title>
          </v-list-item>
          <v-list-item>
            <v-list-item-title>Logout</v-list-item-title>
          </v-list-item>
        </v-list>
      </v-menu>
    </v-app-bar>
    <v-navigation-drawer v-model="drawer" dark app color="#a19e9e">
      <v-layout column align-center>
        <v-flex class="mt-5">
          <v-avatar size="100">
            <img src="/img1.png" alt="" />
          </v-avatar>
          <p class="white--text subheading mt-1 text-center">Username</p>
        </v-flex>
        <v-flex class="mt-4 mb-4">
          <Popup />
        </v-flex>
      </v-layout>
      <v-list flat>
        <v-list-item
          v-for="link in links"
          :key="link.text"
          router
          :to="link.route"
          active-class="border"
        >
          <v-list-item-action>
            <v-icon>{{ link.icon }}</v-icon>
          </v-list-item-action>
          <v-list-item-content>
            <v-list-item-title>{{ link.text }}</v-list-item-title>
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>
  </nav>
</template>
<script>
import Popup from "./Popup.vue";
export default {
  data: () => ({
    drawer: true,
    links: [
      { icon: "home", text: "Home", route: "/" },
      {
        icon: "folder_shared",
        text: "Survei Kepuasan Dosen",
        route: "/projects",
      },
      { icon: "person", text: "Survei Kepuasan", route: "/team" },
    ],
  }),
  components: {
    Popup,
  },
};
</script>
<style scoped>
@import url("https://fonts.googleapis.com/css2?family=Germania+One&family=Poppins:wght@300;400;500;600;700;800;900&family=Roboto&display=swap");
.border {
  border-left: 4px solid #0ba518;
}
#sai {
  font-family: Germania One;
  color: #fff;
  font-size: 25px;
}
</style>
