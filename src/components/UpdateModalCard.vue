<template>
  <div>
    <b-modal ref="my-modal" hide-footer title="Using Component Methods">
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
        class="mt-2"
        variant="outline-warning"
        block
        @click="toggleModal"
        >Update Role Model</b-button
      >
    </b-modal>
  </div>
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
  methods: {
    showModal() {
      this.$refs["my-modal"].show();
    },
    hideModal() {
      this.$refs["my-modal"].hide();
    },
    toggleModal() {
      this.$refs["my-modal"].toggle("#toggle-btn");
      const arr = [
        this.modelName,
        this.modelJob,
        this.modelNationality,
        this.modelBirthday,
        this.modelAbout,
        this.modelPicture,
        this.tags,
      ];
      this.$emit("closeModel", arr);
    },
  },
  mounted() {
    this.showModal();
  },
};
</script>