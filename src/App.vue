<template>
  <div class="container">
    <b-row>
      <b-col sm="4"> <add-role-model /> </b-col>
      <b-col sm="8"> </b-col>
    </b-row>
  </div>
</template>

<script>
import AddRoleModel from "./components/AddRoleModel.vue";
export default {
  name: "App",
  components: {
    AddRoleModel,
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
