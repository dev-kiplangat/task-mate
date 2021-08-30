<template>
  <div class="row items-center justify-between">
    <q-input dense color="teal" outlined v-model="searchText" label="Search">
      <template v-slot:prepend>
        <q-icon name="search" color="orange" />
      </template>
    </q-input>

    <div class="side-icons row items-center justify-between">
      <q-btn icon="people_outline" flat />
      <q-btn icon="mail_outline" flat />
      <q-btn
        label="New Project"
        unelevated
        color="orange"
        class="q-ml-lg"
        no-caps
        @click="$emit('toggle')"
      />
    </div>
  </div>
</template>

<script>
export default {
  name: "top-bar",
  data() {
    return {
      searchText: "",
    };
  },
};
</script>

<style lang="scss" scoped></style>
