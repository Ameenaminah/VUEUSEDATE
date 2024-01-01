<!-- App.vue -->
<template>
  <div class="app-container">
    <h1>{{ value }}</h1>
    <div class="date-container">
      <p>Date: {{ formattedDate }}</p>
      <p>Day: {{ getDay() }}</p>
      <p>Month: {{ getMonth() }}</p>
    </div>
    <div class="button-container">
      <button @click="addDay(1)">Add One Day</button>
      <button @click="addMonth(1)">Add One Month</button>
    </div>
    <div class="input-container">
      <input type="text" v-model="input" @input="handleChange" />
      <button @click="changeTheWorld">Change The World</button>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      input: "",
      value: "HelloWorld",
      date: new Date(),
    };
  },
  computed: {
    formattedDate() {
      const options = { year: "numeric", month: "long", day: "numeric" };
      return this.date.toLocaleDateString(undefined, options);
    },
  },
  methods: {
    getDay() {
      return this.date.getDate();
    },
    getMonth() {
      return this.date.toLocaleString("default", { month: "long" });
    },
    addDay(numberOfDays) {
      const newDate = new Date(this.date);
      newDate.setDate(this.date.getDate() + numberOfDays);
      this.date = newDate;
    },
    addMonth(numberOfMonths) {
      const newDate = new Date(this.date);
      newDate.setMonth(this.date.getMonth() + numberOfMonths);
      this.date = newDate;
    },
    handleChange(event) {
      this.input = event.target.value;
    },
    changeTheWorld() {
      this.value = this.input;
    },
  },
  watch: {
    input(newValue) {
      console.log("Input changed", newValue);
    },
  },
};
</script>

<style scoped>
.app-container {
  max-width: 400px;
  margin: auto;
  text-align: center;
  padding: 20px;
}

h1 {
  font-weight: 800;
  font-size: 1.5rem;
  margin-bottom: 20px;
}

.date-container {
  margin-bottom: 20px;
}

.button-container button {
  margin: 0 10px;
}

.input-container {
  display: flex;
  align-items: center;
  margin-top: 20px;
}

.input-container input {
  flex: 1;
  padding: 8px;
  margin-right: 10px;
}
</style>
