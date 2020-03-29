<template>
  <input :placeholder="placeholder" v-model="input" @keyup.enter="monitorEnterKey"
    class="input is-small" type="text" autofocus />
</template>
<script>
import EventBus from '../EventBus';

export default {
  name: 'InputComponent',
  props: {
    placeholder: String,
  },
  data() {
    return {
      input: '',
    };
  },
  methods: {
    monitorEnterKey() {
      if (this.input.trim() !== '') {
        // this.$emit('add-note', {
        //   note: this.input,
        //   timestamp: (new Date()).toLocaleString(),
        // });

        // Use EventBus instead.
        EventBus.$emit('add-note', {
          note: this.input,
          timestamp: (new Date()).toLocaleString(),
        });
      }
      this.input = '';
    },
  },
};
</script>
<style lang="scss" scoped>
  input {
    text-align: center;
  }
</style>
