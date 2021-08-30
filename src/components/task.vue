<template>
  <div class="custom-card">
    <div class="row items-center justify-between q-pa-md">
      <div class="text-h6">--</div>

      <q-btn color="primary" icon="more_horiz" flat round>
        <q-menu transition-show="jump-down" transition-hide="jump-up">
          <q-list style="max-width: 180px">
            <q-item clickable>
              <q-item-section avatar>
                <q-icon name="edit" />
              </q-item-section>
              <q-item-section>Edit</q-item-section>
            </q-item>
            <q-separator />

            <q-item clickable>
              <q-item-section avatar>
                <q-icon name="checked" />
              </q-item-section>
              <q-item-section>Mark as completed</q-item-section>
            </q-item>
            <q-separator />

            <q-item clickable>
              <q-item-section avatar>
                <q-icon name="delete" />
              </q-item-section>
              <q-item-section>Delete</q-item-section>
            </q-item>
          </q-list>
        </q-menu>
      </q-btn>
    </div>
    <div class="q-pa-md">
      <div class="text-h5">Telemetry Calculator</div>
      <div class="subtitle-text1">Some things just need time!</div>
    </div>
    <div class="q-pa-md row items-center q-gutter-sm">
      <q-avatar size="35px">
        <img src="https://cdn.quasar.dev/img/avatar.png" />
      </q-avatar>

      <q-avatar size="35px">
        <img src="https://cdn.quasar.dev/img/avatar.png" />
      </q-avatar>

      <q-btn icon="add" flat round />
    </div>
  </div>
</template>

<script>
export default {
  name: "task",
};
</script>

<style lang="scss" scoped>
.custom-card {
  max-width: 250px;
  border-radius: 8px;
  background: #eee;
}
</style>
