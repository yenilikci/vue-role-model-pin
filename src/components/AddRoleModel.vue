<template>
  <div class="add-role-model">
    <b-img :src="imageSource" v-bind="mainProps" rounded class="mt-2"></b-img>
    <b-form>
      <b-form-input
        class="mt-2"
        v-model="modelName"
        placeholder="What is your role model name?"
      >
      </b-form-input>
      <b-form-input
        class="mt-2"
        v-model="modelJob"
        placeholder="What is his job?     "
      >
      </b-form-input>
      <b-form-input
        class="mt-2"
        v-model="modelNationality"
        placeholder="What is his nationality?"
      >
      </b-form-input>
      <b-form-input
        class="mt-2"
        v-model="modelPicture"
        placeholder="Add his picture link"
      >
      </b-form-input>
      <label class="mt-2">Choose his birthday:</label>
      <b-form-datepicker
        id="example-datepicker"
        v-model="modelBirthday"
      ></b-form-datepicker>
      <b-form-textarea
        class="mt-2"
        id="textarea"
        v-model="modelAbout"
        placeholder="Notes about him..."
        rows="3"
        max-rows="6"
      ></b-form-textarea>
      <b-form-tags
        input-id="tags-pills"
        v-model="tags"
        tag-variant="primary"
        tag-pills
        separator=" "
        placeholder="Enter new tags separated by space"
        class="mt-2"
      ></b-form-tags>
      <b-button
        @click="sendRoleModel()"
        block
        variant="outline-success"
        class="mt-2"
        >Add</b-button
      >
    </b-form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      modelName: "",
      modelJob: "",
      modelNationality: "",
      modelBirthday: "",
      modelAbout: "",
      modelPicture: "",
      tags: [],
      mainProps: {
        blankColor: "#777",
        width: 150,
        height: 150,
        class: "m1",
      },
      imageSource:
        "https://media.istockphoto.com/vectors/character-with-a-super-hero-shadow-representing-success-in-life-at-vector-id697667340?b=1&k=6&m=697667340&s=612x612&w=0&h=L_fSKXFwtrCN0O_WPTMBFzZpZhzneNXIuKQ_IO1_FBs=",
    };
  },
  methods: {
    sendRoleModel() {
      const arr = [
        this.modelName,
        this.modelJob,
        this.modelNationality,
        this.modelBirthday,
        this.modelAbout,
        this.modelPicture,
        this.tags,
      ];
      this.$emit("fromAddRoleModel", arr);
    },
  },
};
</script>

<style>
.add-role-model {
  display: flex;
  flex-direction: column;
  align-items: center;
}
</style>