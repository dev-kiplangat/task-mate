<template>
  <div class="column b-color">
    <div class="logo"></div>

    <q-list padding class="classic__override">
      <q-item clickable v-ripple :active="active">
        <q-item-section avatar>
          <q-icon name="dashboard" />
        </q-item-section>
        <!-- <q-item-section>Overview</q-item-section> -->
        <!-- <q-item-section side>Side</q-item-section> -->
      </q-item>

      <q-item clickable v-ripple :active="active">
        <q-item-section avatar>
          <q-icon name="task_alt" />
        </q-item-section>
        <!-- <q-item-section>Tasks</q-item-section> -->
        <!-- <q-item-section side>Side</q-item-section> -->
      </q-item>

      <q-item clickable v-ripple :active="active">
        <q-item-section avatar>
          <q-icon name="people" />
        </q-item-section>
        <!-- <q-item-section>Users</q-item-section> -->
        <!-- <q-item-section side>Side</q-item-section> -->
      </q-item>

      <q-item clickable v-ripple :active="active">
        <q-item-section avatar>
          <q-icon name="event" />
        </q-item-section>
        <!-- <q-item-section>Calender</q-item-section> -->
        <!-- <q-item-section side>Side</q-item-section> -->
      </q-item>
    </q-list>
  </div>
</template>

<script>
export default {
  name: "menu-bar",
  data() {
    return {
      active: false,
    };
  },
  methods: {
    flagActive() {
      this.active = this.active ? false : true;
    },
  },
};
</script>

<style lang="scss" scoped>
.logo {
  width: 100%;
  height: 80px;
  position: relative;
}

.logo::after,
.logo::before {
  content: "";
  position: absolute;
}
.logo::before {
  background: aqua;
  top: 10px;
  left: 20px;
  height: 38px;
  width: 12px;
  border-radius: 15px;
  transform: rotate(40deg);
}

.logo::after {
  background: orange;
  top: 15px;
  left: 38px;
  height: 29px;
  width: 12px;
  border-radius: 15px;
  transform: rotate(40deg);
}

.classic__override {
  max-width: 100% !important;
}
.b-color {
  box-shadow: 0 4px 30px rgba(0, 0, 0, 0.13);
  height: 100vh;
}
</style>
