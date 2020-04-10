<template>
  <q-layout view="lHh Lpr lFf">
    <q-header>
      <q-toolbar>
        <q-btn
          flat
          dense
          round
          icon="menu"
          aria-label="Menu"
          @click="leftDrawerOpen = !leftDrawerOpen"
        />

      </q-toolbar>
      <div class="q-px-lg q-pt-xl q-mb-md">
        <div class="text-h3">Todo</div>
        <div class="text-subtitle1">{{todayDate}}</div>
      </div>
      <q-img
        src="statics/icons/city.jpg"
        class="header-image absolute-top"/>

    </q-header>

    <q-drawer
      v-model="leftDrawerOpen"
      show-if-above
      :width="250"
      :breakpoint="600"
    >
      <q-scroll-area style="height: calc(100% - 192px); margin-top: 192px; border-right: 1px solid #ddd">
        <q-list padding >
          <q-item
            to="/"
            exact
            clickable v-ripple>
            <q-item-section avatar>
              <q-icon name="list"/>
            </q-item-section>

            <q-item-section>
              Todo
            </q-item-section>
          </q-item>
          <q-item
            to="/help"
            exact
            clickable v-ripple>
            <q-item-section avatar>
              <q-icon name="help"/>
            </q-item-section>

            <q-item-section>
              help
            </q-item-section>
          </q-item>
          <q-item
            to="github"
            exact
            clickable v-ripple>
            <q-item-section avatar>
              <q-icon name="lab la-github"/>
            </q-item-section>

            <q-item-section>
              GitHub
            </q-item-section>
          </q-item>
        </q-list>
      </q-scroll-area>

      <q-img class="absolute-top" src="statics/icons/city.jpg" style="height: 192px">
        <div class="absolute-bottom bg-transparent">
          <q-avatar size="56px" class="q-mb-sm">
            <img src="https://cdn.quasar.dev/img/boy-avatar.png">
          </q-avatar>
          <div class="text-weight-bold">widade</div>
          <div>@ouidadaziz</div>
        </div>
      </q-img>
    </q-drawer>

    <q-page-container>
      <keep-alive>
        <router-view/>
      </keep-alive>

    </q-page-container>
  </q-layout>
</template>

<script>
  import EssentialLink from 'components/EssentialLink'
  import {date} from 'quasar'

  export default {
    name: 'MainLayout',

    components: {
      EssentialLink
    },
    computed: {
      todayDate() {
        let timeStamp = Date.now()
        return date.formatDate(timeStamp, 'dddd D MMMM ')
      }
    },
    data() {
      return {
        leftDrawerOpen: true
      }
    }

  }

</script>
<style lang="scss">
  .header-image {
    height: 100%;
    z-index: -1;
    opacity: 0.2;
    filter: grayscale(100%);
  }

</style>
