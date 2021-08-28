<template>
  <div class="container">
    <b-row>
      <b-col sm="3">
        <add-role-model @fromAddRoleModel="updateCard($event)" />
      </b-col>
      <b-col sm="9">
        <div class="container p-2">
          <model-card
            v-for="(item, index) in card"
            :key="index"
            :modelName="item[0]"
            :modelJob="item[1]"
            :modelNationality="item[2]"
            :modelBirthDay="item[3]"
            :modelAbout="item[4]"
            :modelPicture="item[5]"
            :tags="item[6]"
          />
        </div>
      </b-col>
    </b-row>
  </div>
</template>

<script>
import globalComponents from "./components/globalComponents";

export default {
  name: "App",
  components: {
    ...globalComponents,
  },
  data() {
    return {
      card: [],
    };
  },
  methods: {
    updateCard(e) {
      this.card.push(e);
    },
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
