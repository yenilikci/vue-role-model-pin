<template>
  <div class="container">
    <b-row>
      <b-col sm="4">
        <div class="container p-2">
          <add-role-model @fromAddRoleModel="updateCard($event)" />
        </div>
      </b-col>
      <transition-group class="role-model" name="role-model" tag="b-col">
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
          @deleteModelOpen="deleteModelOpen($event)"
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
          @hideUpdateModel="hideUpdateModel()"
          :key="randomKey"
        />
        <delete-model-card
          :modelName="card[activeNumber][0]"
          v-if="showModelDelete"
          @deleteModel="deleteModel()"
          @deleteModelHide="deleteModelHide()"
          :index="activeNumber"
          :key="randomKey"
        />
      </transition-group>
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
        showModelDelete: false,
        activeNumber: -1,
        randomKey: Math.random(),
      };
    },
    methods: {
      updateCard(e) {
        this.card.push(e);
      },
      activeIndex(e) {
        this.showModel = true;
        this.activeNumber = e;
      },
      updateOk(e) {
        this.card.splice(this.activeNumber, 1, e);
        this.showModel = false;
        this.activeNumber = -1;
      },
      deleteModelOpen(e) {
        this.showModelDelete = true;
        this.activeNumber = e;
      },
      deleteModel() {
        this.card.splice(this.activeNumber, 1);
        this.showModelDelete = false;
        this.activeNumber = -1;
      },
      deleteModelHide() {
        this.showModelDelete = false;
      },
      hideUpdateModel() {
        this.showModel = false;
      },
    },
  };
</script>

<style>
  .role-model {
    margin-top: 10px;
    backface-visibility: hidden;
    transform-origin: 10% 50%;
    z-index: 1;
  }
  .role-model-move {
    transition: all 600ms ease-out;
  }
  .role-model-enter-active {
    transition: all 300ms ease-out;
  }
  .role-model-leave-active {
    transition: all 200ms ease-out;
    position: absolute;
    z-index: 1;
  }
  .role-model-enter,
  .role-model-leave-to {
    opacity: 0;
  }
</style>
