<template>
  <div class="search-select" :class="{ 'is-active': isOpen }">
    <button @click="open" type="button" class="search-select-input">
      <span v-if="value !== null">{{ value }}</span>
      <span v-else class="search-select-placeholder">Select Soldier</span>
    </button>
    <div v-show="isOpen" class="search-select-dropdown">
      <input class="search-select-search" />
      <ul class="search-select-options">
        <li
          class="search-select-option"
          v-for="option in options"
          :key="option"
          @click="select(option)"
        >
          {{ option }}
        </li>
      </ul>
      <!-- <div class="search-select-empty">No results found</div> -->
    </div>
  </div>
</template>
<script>
export default {
  data() {
    return {
      isOpen: false,
      value: null,
      options: [
        "1LT Lakes, Dale",
        "1LT Ball, Michael",
        "CW3 Latane, Paul",
        "SFC Busby, Ryan",
        "SSG Salinas, Ricky",
        "SSG Hochheimer, Steven",
        "SSG Fossett, Matt",
        "SSG Sabatini, Jesse",
        "SSG jackson, Jeremy"
      ]
    };
  },
  methods: {
    open() {
      this.isOpen = true;
    },
    close() {
      this.isOpen = false;
    },
    select(option) {
      this.value = option;
      this.close();
    }
  },
  computed: {
    hope: function () {
      return this.value;
    }
  }
};
</script>