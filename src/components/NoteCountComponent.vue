<template>
  <div class="note-count">Note count: <strong>{{ noteCount }}</strong></div>
</template>
<script>
import EventBus from '../EventBus';

export default {
  name: 'NoteCountComponent',
  data() {
    return {
      noteCount: 0,
    };
  },
  created() {
    // Use EventBus.
    EventBus.$on('add-note', () => {
      this.noteCount += 1;
    });
  },
};
</script>
<style lang="scss" scoped></style>
