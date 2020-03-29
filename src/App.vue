<template>
  <div id="app">
    <div class="notes-section">
      <div class="columns">
        <div class="column has-text-centered">
          <strong>Notes</strong>
          <div v-for="(note, index) in notes" :key="index" class="notes">
            {{ note }}
          </div>
        </div>
        <div class="column has-text-centered">
          <strong>Timestamp</strong>
          <div v-for="(timestamp, index) in timestamps" :key="index" class="timestamps">
            {{ timestamp }}
          </div>
        </div>
      </div>
      <!-- <InputComponent :placeholder="placeholder" @add-note="addNote" /> -->
      <InputComponent :placeholder="placeholder" /> <!-- Use EventBus instead. -->
    </div>
    <NoteCountComponent />
  </div>
</template>
<script>
import EventBus from './EventBus';
import InputComponent from './components/InputComponent.vue';
import NoteCountComponent from './components/NoteCountComponent.vue';

export default {
  name: 'App',
  components: {
    InputComponent,
    NoteCountComponent,
  },
  data() {
    return {
      notes: [],
      timestamps: [],
      placeholder: 'Enter a note',
    };
  },
  methods: {
    addNote(event) {
      this.notes.push(event.note);
      this.timestamps.push(event.timestamp);
    },
  },
  created() {
    // Use EventBus instead.
    EventBus.$on('add-note', (event) => {
      this.addNote(event);
    });
  },
};

</script>
<style lang="scss"></style>
