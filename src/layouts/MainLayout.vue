<template>
  <q-layout view="lHh Lpr lFf">
    <q-header elevated class="bg-purple">
      <!-- checkpoint 1 (a) -->
      <q-toolbar>
        <q-toolbar-title> My first App </q-toolbar-title>

        <div>{{ data.date }}</div>
        <q-btn
          class="q-ml-sm"
          flat
          round
          dense
          icon="home"
          @click="$router.replace('/')"
        />
        <!-- checkpoint 1 (b) -->
      </q-toolbar>
    </q-header>

    <q-footer elevated>
      <q-toolbar>
        <q-toolbar-title
          >โควิทวันนี้
          <q-chip
            color="orange"
            text-color="white"
            icon-right="health_and_safety"
          >
            <b> รายใหม่: {{ data.new_case }}</b>
          </q-chip>
          <q-chip
            color="red"
            text-color="white"
            icon-right="sentiment_very_dissatisfied"
          >
            <b> เสียชีวิต: {{ data.new_death }}</b>
          </q-chip>
          </q-toolbar-title
        >
        <div>จัดทำโดย: นายณัฐนัย ยาพระจันทร์ <b>6210110107</b></div>
      </q-toolbar>
    </q-footer>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script>
import { defineComponent, ref } from "vue";
import { useQuasar, date } from "quasar";

export default defineComponent({
  name: "MainLayout",

  setup() {
    const leftDrawerOpen = ref(false);
    const data = ref({
      date: date.formatDate(Date.now(), "DD MMMM YYYY"),
      new_case: 0,
      new_death: 0,
    });
    const $q = useQuasar();

    fetch(`https://covid19.ddc.moph.go.th/api/Cases/today-cases-all`)
      .then((response) => response.json())
      .then((json) => {
        data.value.new_case = json[0].new_case;
        data.value.new_death = json[0].new_death;
      })
      .catch((error) => {
        console.warn(error);
      });

    return {
      data,
      essentialLinks: linksList,
      leftDrawerOpen,
      toggleLeftDrawer() {
        leftDrawerOpen.value = !leftDrawerOpen.value;
      },
    };
  },
});
</script>
