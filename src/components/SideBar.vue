<template>
    <v-navigation-drawer expand-on-hover rail v-if="false">

        <v-list>
          <v-list-item
            prepend-avatar="https://randomuser.me/api/portraits/women/85.jpg"
            title="R Michelon"
            subtitle="/raquelmichelon"
          ></v-list-item>
        </v-list>

        <v-list density="compact" nav>
          <v-list-item prepend-icon="mdi-pencil" title="My Notes" value="mynotes"></v-list-item>
          <v-list-item prepend-icon="mdi-account-multiple" title="Shared with me" value="shared"></v-list-item>
          <v-list-item prepend-icon="mdi-star" title="Starred" value="starred"></v-list-item>
        </v-list>

        <v-divider></v-divider>
    </v-navigation-drawer>
</template>