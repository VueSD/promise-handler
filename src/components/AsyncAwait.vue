<script>
export default {
  props: {
    promise: {
      type: Promise,
      required: true
    }
  },

  data: () => ({
    state: {
      isLoading: false,
      error: null,
      results: null
    }
  }),

  async mounted() {
    try {
      this.state.isLoading = true;
      this.state.results = await this.promise;
    } catch (error) {
      this.state.error = error;
    } finally {
      this.state.isLoading = false;
    }
  },

  render() {
    return this.$scopedSlots.default({
      ...this.state
    });
  }
};
</script>
