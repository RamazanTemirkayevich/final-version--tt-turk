<template>
  <div>
    <ul class="promo-size__items">
      <li 
        v-for="tab in tabs" 
        :key="tab"
        class="promo-size__items--index" 
        :class="{ active: tab === selected }" 
        @click="setTab(tab)"
      >{{ tab }}
      </li>
    </ul>

    <slot></slot>
  </div>
</template>

<script>
export default {
  props: {
    /* Holds all of the tabs data */
    tabs: {
      type: Array,
      required: true,
    },
    selected: {
      type: String,
      required: true,
    }
  },
  methods: {
    setTab(tab) {
      this.$emit('selected', tab);
    },
  },
};
</script>