<template>
  <b-card
    :title="modelName"
    :img-src="modelPicture"
    img-alt="Image"
    img-top
    tag="article"
    style="max-width: 20rem"
    class="mb-2"
  >
    <b-card-text>
      {{ modelJob }} - {{ modelNationality }} - {{ modelBirthday }}
    </b-card-text>
    <b-card-text>
      {{ modelAbout }}
    </b-card-text>
    <div class="tagsClass my-3">
      <b-card-text class="tagsText" v-for="(tag, index) in tags" :key="index">
        {{ tag }}
      </b-card-text>
    </div>

    <b-button href="#" variant="primary">Go somewhere</b-button>
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
  },
  data() {
    return {};
  },
};
</script>

<style>
.tagsClass {
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
}
.tagsText {
  background-color: rgb(132, 170, 209);
  margin: 3px;
  font-size: 16px;
  font-family: Arial, Helvetica, sans-serif;
  padding: 4px;
  box-shadow: 0 0 4px rgb(92, 92, 223);
  color: #fff;
}
</style>