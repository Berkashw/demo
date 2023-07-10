<template>
  <div @submit.prevent class="root">
    <div class="grid">
      <input
        @keyup.enter="getResult()"
        type="text"
        v-model="mainInput"
        placeholder="0"
      />
      <button @click="clearInput()" class="cell op">C</button>
      <button @click="getSqrt()" class="cell op">sqrt</button>
      <button @click="delLast()" class="cell op">Backspace</button>
      <button
        @click="addChar(num)"
        class="cell num"
        v-for="num in numbers"
        v-bind:key="num"
      >
        {{ num }}
      </button>
      <button
        @click="addChar(op)"
        class="cell op"
        v-for="op in operations"
        v-bind:key="op"
      >
        {{ op }}
      </button>
      <button @click="getResult()" class="cell op">=</button>
    </div>
  </div>
</template>
<script>
export default {
  name: "Calculator",
  components: {},
  data() {
    return {
      mainInput: "",
      numbers: [1, 2, 3, 4, 5, 6, 7, 8, 9, 0, "."],
      operations: ["+", "-", "*", "/", "(", ")"],
    };
  },
  methods: {
    addChar(btnChar) {
      this.mainInput = this.mainInput.toString();
      this.mainInput += btnChar;
    },
    clearInput() {
      this.mainInput = "";
    },
    getResult() {
      this.mainInput = eval(this.mainInput);
      this.mainInput.toString();
      return this.mainInput;
    },
    getSqrt() {
      return (this.mainInput = Math.sqrt(eval(this.mainInput)));
    },
    delLast() {
      return (this.mainInput = this.mainInput.slice(0, -1));
    },
  },
};
</script>

<style>
* {
  font-family: "Gilroy", sans-serif;
  transition: 0.3s all;
  font-weight: 600;
}
#app {
  width: 300px;
  box-shadow: 0 3px 15x rgb(74, 62, 62);
}
input {
  width: 300px;
  border: 1;
  color: #207d61;
  font-size: 18px;
  padding: 5px 5px;
  text-align: right;
}

.grid {
  display: flex;
  flex-wrap: wrap;
  justify-content: space-around;
  width: 100%;
}
.cell {
  flex: 26%;
  height: 50px;
  font-size: 18px;
  border: 0;
}
.num {
  background-color: #5e80a2;
  color: #e0eef4;
  font-weight: 400;
}
.cell:hover {
  background-color: #afc9df;
}
.op {
  background-color: #dcf0f0;
  color: #243849;
}
</style>
