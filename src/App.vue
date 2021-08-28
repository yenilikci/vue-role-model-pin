<template>
  <div class="container">
    <b-row>
      <b-col sm="4">
        <div class="container p-2">
          <add-role-model @fromAddRoleModel="updateCard($event)" />
        </div>
      </b-col>
      <b-col sm="8">
        <div class="container p-2">
          <model-card
            v-for="(item, index) in card"
            :key="index"
            :index="index"
            :modelName="item[0]"
            :modelJob="item[1]"
            :modelNationality="item[2]"
            :modelBirthDay="item[3]"
            :modelAbout="item[4]"
            :modelPicture="item[5]"
            :tags="item[6]"
            @updateEmitIndex="activeIndex($event)"
          />
          <update-modal-card
            :modelName="card[activeNumber][0]"
            :modelJob="card[activeNumber][1]"
            :modelNationality="card[activeNumber][2]"
            :modelBirthDay="card[activeNumber][3]"
            :modelAbout="card[activeNumber][4]"
            :modelPicture="card[activeNumber][5]"
            :tags="card[activeNumber][6]"
            v-if="showModel"
            @closeModel="updateOk($event)"
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
      showModel: false,
      activeNumber: -1,
    };
  },
  methods: {
    updateCard(e) {
      this.card.push(e);
    },
    activeIndex(e) {
      this.showModel = true;
      this.activeNumber = e;
      console.log(e);
    },
    updateOk(e) {
      this.card.splice(this.activeNumber, 1, e);
      this.showModel = false;
      this.activeNumber = -1;
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
