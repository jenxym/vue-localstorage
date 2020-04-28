<template>
  <v-app>
    <v-app-bar app color="primary" dark>
      <div class="d-flex align-center">
        <v-img alt="Vuetify Logo" class="shrink mr-2" contain src="https://cdn.vuetifyjs.com/images/logos/vuetify-logo-dark.png" transition="scale-transition" width="40" />
        <h1 class="mt-1">Simple Task Manager</h1>
      </div>
      <v-spacer></v-spacer>
      <v-btn href="https://github.com/jenxym/vue-localstorage" target="_blank" text>
        <span class="mr-2">Github Repo</span>
        <v-icon>mdi-open-in-new</v-icon>
      </v-btn>
    </v-app-bar>

    <v-content>
      <TaskSetter />
      <TasksList />
    </v-content>
  </v-app>
</template>

<script>
import TasksList from "./components/TasksList";
import TaskSetter from "./components/TaskSetter";

export default {
  name: "App",

  components: {
    TasksList,
    TaskSetter,
  },

  data: () => ({
    //
  }),
};
</script>
