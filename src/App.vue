<template>
  <div class="root">
    <ul>
      <li>
        <p @click="showCalc = !showCalc">1.Калькулятор</p>
        <transition>
          <calculator v-if="showCalc"> </calculator>
        </transition>
      </li>
    </ul>
  </div>
</template>

<script>
import Calculator from "./components/Calculator.vue";
export default {
  components: { Calculator },
  data() {
    return {
      showCalc: false,
    };
  },
};
</script>

<style>
.root {
  border: 1cm;
}
</style>
