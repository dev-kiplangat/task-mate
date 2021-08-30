<template>
  <div class="container">
    <!-- side menu -->
    <side-menu />
    <!-- project summary -->
    <project-info />

    <!-- content -->
    <project-dashboard />
  </div>
</template>

<script>
import sideMenu from "@/components/menu-bar.vue";
import projectInfo from "@/components/project-info.vue";
import homeContent from "@/components/homeContent.vue";

export default {
  name: "Home",
  components: {
    "side-menu": sideMenu,
    "project-info": projectInfo,
    "project-dashboard": homeContent,
  },
};
</script>

<style lang="scss">
.container {
  display: grid;
  grid-template-columns: 65px 300px auto;
}
</style>
