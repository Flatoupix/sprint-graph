<template>
  <div id="app">
    <div>
      <v-text-field
        @keypress.enter="inputValue(txtValue)"
        class="w-50"
        v-model="txtValue"
        label="Regular"
      ></v-text-field>
    </div>
    <v-card max-width="344" class="mx-auto">
      <v-card-title>{{ sprint01.name }}</v-card-title>
      <v-card-text>{{ sprint01.description }}</v-card-text>
      <div v-if="opened">
        <v-chip
          close
          @click:close="removeValue(member)"
          v-for="(member, id) in sprint01.members"
          :key="id"
          >{{ member }}</v-chip
        >
      </div>
      <v-card-actions>
        <v-btn text @click="opened = !opened">Click</v-btn>
      </v-card-actions>
    </v-card>
  </div>
</template>

<script>
export default {
  name: "app",
  data() {
    return {
      opened: false,
      sprint01: {
        name: "Sprint TEST01",
        start: "02-05-20",
        end: "15-05-20",
        members: ["Gerard", "Paul", "Lucien", "Jean-Christophe"],
        description: "Description"
      },
      txtValue: "Bonjour"
    };
  },
  components: {},
  methods: {
    inputValue(txt) {
      this.sprint01.members.push(txt);
    },
    removeValue(txt) {
      this.sprint01.members.splice(txt, 1);
    }
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
