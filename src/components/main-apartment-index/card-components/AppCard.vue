<script>
import AppCarosel from "./AppCarosel.vue";
import { store } from '../../../store';

export default {
  name: "AppCard",
  components: {
    AppCarosel,
  },
  props: {
    data: Object,
  },
  data() {
    return {
      store,
    }
  }
};
</script>

<template>
  <router-link
    :to="{ name: 'apartment-page', params: { slug: data.slug } }"
    class="single-apartment text-dark text-decoration-none d-block mb-5"
  >
    <div class="ms-card">
      <img class="ms-card__image rounded-4 mb-3" :src="data.image_url" alt="" />

      <div class="ms-card__information">
        <h6 class="fw-bold">{{ data.title }}</h6>
        <div class="text-muted">{{ data.mq }} metri quadrati</div>
        <div class="text-muted my-1">{{ data.full_address }}</div>
        <div class="my-1">
          <strong>Servizi: </strong>
          <span class="text-muted" v-for="(service, index) in data.services">
            {{ index == data.services.length - 1 ? service.name : service.name + ', ' }}
          </span> 
        </div>
        <div class="text-muted">
          <strong class="text-dark">{{ data.price }} €</strong> notte
        </div>
      </div>
    </div>
  </router-link>
</template>

<style lang="scss" scoped>
.ms-card {
  width: 100%;
  height: 100%;
  img {
    object-fit: cover;
    width: 100%;
    height: 310px;
  }
}
</style>
