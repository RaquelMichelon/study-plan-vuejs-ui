<script setup>
import NavBar from './components/NavBar.vue'
import SideBar from './components/SideBar.vue'
import {ref} from 'vue'

const newSubject = ref("")

const titleSubject = ref("")
const showPlan = ref(false)
const selected = ref([])

const text = ref("1. Understand the Roman Republic and its political and social structures. 2. Learn about the major events and people of the Roman Empire, including the Pax Romana. 3. Familiarize yourself with Roman culture and society, including language, art, architecture, literature, law, and religion. 4. Study the Roman military, its tactics and organization, and its effects on the empire. 5. Examine the decline of the Roman Empire, its eventual fall, and its legacy.".split(/[0-9.]\./g).filter((value) => !!value))

// show created plan
const createPlan = ()=>{
    if(newSubject.value == "") {
      return
    } else {
      showPlan.value = true
      titleSubject.value = newSubject.value
      newSubject.value = " "
    }
}

const cleanPlan = ()=>{
  showPlan.value = false
}



</script>

<template>
 <v-app>
  <!-- NAVBAR COMPONENT -->
  <NavBar />

  <!-- SIDEBAR COMPONENT -->
  <SideBar />

  <!-- STUDY PLAN COMPONENT -->
  <v-main>
     
     <v-container>
     
     <v-row no-gutters justify="center">
      <v-sheet width="450" class="pa-2 ma-3">
        <v-form @submit.prevent="createPlan" ref="form">
          <v-text-field
            v-model="newSubject"
            :rules="[v => !!v || 'This field is required']"
            label="Type a subject to get your study plan"
          ></v-text-field>
            <v-btn type="submit" block class="mt-2" prepend-icon="mdi-check-circle">Create Plan</v-btn>
        </v-form>
      </v-sheet>
      </v-row>

      <v-row no-gutters justify="center" v-if="showPlan">
      <v-col cols="8" >
        <v-sheet class="pa-2 ma-2">
          <p class="text-h4 pa-3 text-center bg-amber-lighten-5"> Study Plan for <strong> {{ titleSubject !== "" ? titleSubject : "..." }} </strong> </p>
          <v-container fluid class="bg-amber-lighten-5">
          <!-- <p>{{ selected }}</p> -->
          <v-checkbox
            v-for="(item, index) in text" :key="index"
            v-model="selected"
            :label="item"
            :value="index"
          ></v-checkbox>
        </v-container>
        </v-sheet>
      </v-col>
    </v-row>

    <v-row no-gutters justify="center" v-if="showPlan">
     <v-col cols="auto">
        <v-btn prepend-icon="mdi-delete" color="red" @click="cleanPlan">Delete Plan</v-btn>
      </v-col>
    </v-row>
     
     </v-container>

  </v-main>

 </v-app>
</template>

