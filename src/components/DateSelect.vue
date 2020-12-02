<template>
  <div id="app">
    {{ date }}
    <br />
    <br />
    <Datepicker
      placeholder="Select Friday in Week Of:"
      v-if="date"
      :disabled-dates="disabledDates"
    />
  </div>
</template>

<script>
import Datepicker from "vuejs-datepicker/dist/vuejs-datepicker.esm.js";

export default {
  // date: 'SelectedDate',
  data() {
    return {
      value: "",
      today: new Date(),
      date: null,
      disabledDates: {
        days: [0, 1, 2, 3, 4, 6]
      },
      highlighted: {
        days: [5]
      }
    };
  },

  components: {
    Datepicker
  },

  methods: {
    getDateByDay(currDate, day, week = 0) {
      var reqDate = currDate;
      return {
        day: reqDate.getDate(),
        month: reqDate.getMonth(),
        year: reqDate.getFullYear()
      };
    },

    strategy({ year }) {
      this.date = Date(year);
    }
  },

  mounted() {
    this.strategy({ year: 1 });
  }
};
</script>