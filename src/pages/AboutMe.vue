<template> 
  <q-page padding>
    <q-card class="my-card">
      <q-card-section>
        Hello world!
      </q-card-section>
    </q-card>
    <q-btn
      color="primary"
      icon="home"
      label="Go Home"
      @click="$router.replace('/')"
    />
  </q-page>
</template>

<script>
export default {
  // name: 'PageName',
};
</script>
