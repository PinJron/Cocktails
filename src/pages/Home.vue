<script setup>
import AppLayout from '@/components/AppLayout.vue';
import { useRootStore } from '@/stores/root';
import { storeToRefs } from 'pinia';
import { ref } from 'vue';

const rootStore = useRootStore()
rootStore.getIngredients()

const {ingredients} = storeToRefs(rootStore);
const ingredient = ref(null)
</script>

<template>
  <AppLayout imgUrl="/src/assets/img/bg-1.jpg">
    <div class="wrapper">
      <div class="info">
        <div class="title">Chose your drink</div>
        <div class="line"></div>
        <div class="select-wrapper"></div>
          <el-select 
            v-model="ingredient" 
            placeholder="Choose main ingredient" 
            size="large"
            class="select"
          >
            <el-option
              v-for="item in ingredients"
              :key="item.strIngredient1"
              :label="item.strIngredient1"
              :value="item.strIngredient1"
            />
          </el-select>
          <div class="text">
            Try our delicious cocktail recipes for every occasion. 
            Find delicious cocktail recipes by ingredient through our 
            cocktail generator.
          </div>
      </div>
    </div>
  </AppLayout>
</template>

<style lang="sass" scoped>
@import '../assets/styles/main'

.wrapper
  display: flex
  justify-content: center
  align-items: center

.info
  padding: 80px 0
  text-align: center

.select-wrapper
  padding-top: 50px

.select
  width: 220px

.text
  max-width: 516px
  padding-top: 50px
  margin: 0 auto
  line-height: 36px
  letter-spacing: 0.1em
  color: $textMuted
</style>