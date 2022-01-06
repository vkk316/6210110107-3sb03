<template>
  <div>
    <!-- checkpoint 2 : add carousel  -->
    <q-carousel
      animated
      v-model="slide"
      navigation
      infinite
      :autoplay="autoplay"
      arrows
      transition-prev="slide-right"
      transition-next="slide-left"
      @mouseenter="autoplay = false"
      @mouseleave="autoplay = true"
    >
      <q-carousel-slide
        :name="1"
        img-src="https://cdn.pixabay.com/photo/2020/03/19/21/35/covid-4948866_960_720.jpg"
      />
      <q-carousel-slide
        :name="2"
        img-src="https://cdn.pixabay.com/photo/2021/01/19/17/59/mask-5932015_960_720.png"
      />
      <q-carousel-slide
        :name="3"
        img-src="https://cdn.pixabay.com/photo/2021/12/07/10/26/corona-6852923_960_720.jpg"
      />
      <q-carousel-slide
        :name="4"
        img-src="https://cdn.pixabay.com/photo/2018/03/22/23/21/cute-3252251_960_720.jpg"
      />
    </q-carousel>
    <div class="q-pa-md flex flex-center">
      <!-- checkpoint 2 : about me button  -->
      <q-btn
        unelevated
        rounded
        icon="account_circle"
        color="primary"
        label="ABOUT ME"
        @click="$router.replace('/aboutme')"
      />
    </div>
  </div>
</template>

<script>
import { defineComponent } from "vue";
import { ref } from "vue";
export default defineComponent({
  name: "PageIndex",
  setup() {
    return {
      slide: ref(1),
      autoplay: ref(true),
    };
  },
});
</script>
