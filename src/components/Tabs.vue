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