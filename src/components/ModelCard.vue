<template>
  <b-card
    :title="modelName"
    :img-src="modelPicture"
    img-top
    tag="article"
    class="shadow mb-2"
  >
    <b-card-text>
      {{ modelJob }} - {{ modelNationality }} - {{ modelBirthday }}
    </b-card-text>
    <b-card-text>
      {{ modelAbout }}
    </b-card-text>
    <div class="tagsClass my-3">
      <b-card-text class="tagsText" v-for="(tag, index) in tags" :key="index">
        #{{ tag }}
      </b-card-text>
    </div>

    <div class="bottomButtons">
      <b-button @click="updateEmitIndex()" variant="outline-success"
        >Update</b-button
      >
      <b-button variant="outline-danger">Delete</b-button>
    </div>
  </b-card>
</template>

<script>
export default {
  props: {
    modelName: String,
    modelJob: String,
    modelNationality: String,
    modelBirthday: String,
    modelAbout: String,
    modelPicture: String,
    tags: Array,
    index: Number,
  },
  data() {
    return {};
  },
  methods: {
    updateEmitIndex() {
      this.$emit("updateEmitIndex", this.index);
    },
  },
};
</script>

<style>
.tagsClass {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
}
.tagsText {
  background-color: rgb(132, 170, 209);
  margin: 3px;
  font-size: 14px;
  font-family: Arial, Helvetica, sans-serif;
  padding: 5px;
  border-radius: 16px;
  box-shadow: 0 0 4px rgb(92, 92, 223);
  color: #fff;
}
.card-text:last-child {
  margin-bottom: 3px !important;
}
.bottomButtons {
  display: flex;
  flex-direction: row;
  justify-content: space-between;
}
</style>