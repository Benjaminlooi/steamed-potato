<template>
  <v-app>
    <v-navigation-drawer app>
      <v-list nav dense>
        <v-list-item-group active-class="deep-purple--text text--accent-4">
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

    <v-app-bar app>
      <v-app-bar-nav-icon></v-app-bar-nav-icon>

      <v-toolbar-title>Steamed Potato</v-toolbar-title>
    </v-app-bar>

    <!-- Sizes your content based upon application components -->
    <v-main>
      <!-- Provides the application the proper gutter -->
      <v-container fluid>
        <Nuxt />
      </v-container>
    </v-main>

    <v-footer app padless>
      <v-card flat tile width="100%" class="grey lighten-5 text-center">
        <v-divider></v-divider>

        <v-card-text>
          {{ new Date().getFullYear() }} —
          <strong><a href="https://benjaminlooi.dev">Benjamin Looi</a></strong>
        </v-card-text>
      </v-card>
    </v-footer>
  </v-app>
</template>
