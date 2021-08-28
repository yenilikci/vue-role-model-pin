<template>
  <div>
    <b-modal
      ref="my-modal"
      hide-footer
      :title="modelName + '  Role Model Card'"
      @hidden="hideModal()"
    >
      <b-button
        class="mt-2"
        variant="outline-warning"
        block
        @click="toggleModal"
        >Delete Role Model</b-button
      >
    </b-modal>
  </div>
</template>

<script>
export default {
  props: {
    index: Number,
    modelName: String,
  },
  methods: {
    showModal() {
      this.$refs["my-modal"].show();
    },
    hideModal() {
      this.$refs["my-modal"].hide();
      this.$emit("deleteModelHide");
    },
    toggleModal() {
      this.$refs["my-modal"].toggle("#toggle-btn");
      this.$emit("deleteModel");
    },
  },
  mounted() {
    this.showModal();
  },
};
</script>