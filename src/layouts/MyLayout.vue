<template>
  <q-layout view="lHh Lpr lFf">
    <q-header>
      <q-toolbar>
        <q-btn
          flat
          dense
          round
          @click="leftDrawerOpen = !leftDrawerOpen"
          icon="menu"
          aria-label="Menu"
        />

        <q-toolbar-title>Quasar App</q-toolbar-title>

        <div>Quasar v{{ $q.version }}</div>
      </q-toolbar>
      <div class="q-px-lg q-pt-xl q-mb-md">
        <div class="text-h3">Todo</div>
        <div class="text-subtitle1">{{ todaysDate }}</div>
      </div>
      <q-img src="../statics/analytics.jpg" class="header-image absolute-top" />
    </q-header>

    <q-drawer v-model="leftDrawerOpen" show-if-above :width="250" :breakpoint="600">
      <q-scroll-area
        style="height: calc(100% - 180px); margin-top: 180px; border-right: 1px solid #ddd"
      >
        <q-list padding>
          <q-item clickable v-ripple>
            <q-item-section avatar>
              <q-icon name="list" />
            </q-item-section>

            <q-item-section>Todo</q-item-section>
          </q-item>
          <q-item clickable v-ripple>
            <q-item-section avatar>
              <q-icon name="help" />
            </q-item-section>

            <q-item-section>Help</q-item-section>
          </q-item>
        </q-list>
      </q-scroll-area>

      <q-img class="absolute-top" src="../statics/analytics - rev.jpg" style="height: 180px">
        <div class="absolute-bottom bg-transparent">
          <q-avatar size="56px" class="q-mb-sm">
            <img src="https://cdn.pixabay.com/photo/2015/11/15/07/47/geometry-1044090_960_720.jpg" />
          </q-avatar>
          <div class="text-weight-bold">Bartlomiej Wydmuch</div>
          <div>@bartekcostam</div>
        </div>
      </q-img>
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script>
import { date } from "quasar";
export default {
  name: "MyLayout",

  data() {
    return {
      leftDrawerOpen: false
    };
  },
  computed: {
    todaysDate() {
      let timeStamp = Date.now();
      return date.formatDate(timeStamp, "dddd D MMMM");
    }
  }
};
</script>


<style lang="scss">
.header-image {
  height: 100%;
  z-index: -1;
  opacity: 0.4;
}
</style>