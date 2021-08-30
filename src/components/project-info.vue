<template>
  <div class="main q-py-lg">
    <!-- avatar -->
    <div class="column items-center justify-center">
      <div class="avatar row items-center justify-center">
        <span>U</span>
        <span>A</span>
      </div>

      <div class="text-h6">Utsman Affan</div>
    </div>

    <!-- title -->

    <!-- progress bar -->
    <div class="q-pa-md">
      <div class="text-h6 row items-center justify-between">
        <span> progress</span>
        <span>{{ progress }} %</span>
      </div>
      <q-slider
        snap
        class="classic__override"
        v-model="lazy"
        :min="0"
        readonly
        :max="45"
        :step="5"
        color="light-green"
        value="lazy"
        label
      />
    </div>

    <!-- calender -->
    <div class="q-pa-md">
      <div class="text-h6 q-mb-md">Project Timeline</div>
      <q-date
        readonly
        class="classic__override max-height"
        v-model="model"
        range
        minimal
        color="orange"
      />
    </div>
  </div>
</template>

<script>
export default {
  name: "project-info",
  data() {
    return {
      model: { from: "2020/07/08", to: "2020/07/17" },
      lazy: 6,
      max: 45,
    };
  },
  computed: {
    progress() {
      return parseInt((this.lazy / this.max) * 100);
    },
  },
};
</script>

<style lang="scss" scoped>
.classic__override {
  min-width: 100% !important;
}

.avatar {
  width: 120px;
  height: 120px;
  border-radius: 50%;
  background: rgba(0, 0, 0, 0.226);
  font-size: 40px;
}
</style>
