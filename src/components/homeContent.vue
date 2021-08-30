<template>
  <div class="q-pa-lg q-pl-lg">
    <top-bar @toggle="toggle" />

    <!-- content follows -->

    <!-- create Task modal -->
    <create-task @toggle="toggle" :dialog="dialog" />

    <main class="content q-pa-lg">
      <div class="row items-center justify-between">
        <div class="text-h6">Utsman Affan</div>
      </div>

      <div style="max-width: 600px">
        <q-tabs v-model="tab" align="left" narrow-indicator class="q-mb-lg">
          <q-tab class="text-purple" name="tasks" label="Tasks" />
          <q-tab class="text-teal" name="issues" label="issues" />
          <q-tab class="text-orange" name="goals" label="goals" />
          <q-tab class="text-teal" name="chats" label="chats" />
        </q-tabs>

        <div class="q-gutter-y-sm">
          <q-tab-panels
            v-model="tab"
            animated
            transition-prev="scale"
            transition-next="scale"
            class="text-white text-center"
          >
            <q-tab-panel name="tasks">
              <tasks-panel />
            </q-tab-panel>

            <q-tab-panel name="issues">
              <issue />
            </q-tab-panel>

            <q-tab-panel name="goals">
              <div class="text-h6">Alarms</div>
              Ad molestiae non facere animi nobis, similique nemo velit
              reiciendis corporis impedit nam in.
            </q-tab-panel>

            <q-tab-panel name="chats">
              <div class="text-h6">Movies</div>
              Nostrum necessitatibus expedita dolores? Voluptatem repudiandae
              magni ea.
            </q-tab-panel>
          </q-tab-panels>
        </div>
      </div>
    </main>
  </div>
</template>

<script>
import topBar from "@/components/top-bar.vue";
import TasksPanel from "@/components/tasks-panel.vue";
import createTask from "@/components/create-task.vue";
import issue from "@/components/issue.vue";

export default {
  name: "homeContent",
  components: {
    "top-bar": topBar,
    "tasks-panel": TasksPanel,
    "create-task": createTask,
    issue,
  },

  data() {
    return {
      tab: "tasks",
      dialog: false,
    };
  },
  methods: {
    toggle() {
      this.dialog = this.dialog ? false : true;
    },
  },
};
</script>

<style lang="scss" scoped></style>
