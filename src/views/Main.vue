 <script setup>
import { onMounted, ref } from "vue";
import Categories from "@/components/Categories.vue";
import Pizza from "@/components/PizzaBlock/Pizza.vue";
import Sort from "@/components/Sort.vue";
import { useStore } from "vuex";
const store = useStore();

onMounted(() => {
  store.commit("SET_PIZZAS");
});
</script>

<template>
  <div class="content">
    <div class="container">
      <div class="content__top">
        <Categories
          @filter="(e) => store.commit('CHANGE_FILTERED_PIZZAS', e)"
        />
        <Sort />
      </div>
      <h2 class="content__title">Все пиццы</h2>
      <div class="content__items">
        <Pizza
          v-for="item in store.state.filteredPizzas"
          :key="item.id"
          :pizza="item"
        />
      </div>
    </div>
  </div>
</template>
