<script setup>
import axios from 'axios';

import DataTable from './components/DataTable.vue'
</script>

<template>
  <header>
    <div class="wrapper">
      <DataTable 
        :events="events" />
    </div>
  </header>
</template>

<script>
export default {
  name: 'app',
  data() {
    return {
      events: [],
    }
  },
  async created() {
    [
      { data: this.events }, 
    ] = await axios.all([
      axios.get(
        '/events.json'  
      ), 
    ]);
  },
}
</script>
