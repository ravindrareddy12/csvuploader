<template>
  <CsvUploader />
</template>

<script>
import { defineComponent } from 'vue';

// Components
import CsvUploader from '../components/CsvUploader.vue';

export default defineComponent({
  name: 'HomeView',

  components: {
    CsvUploader,
  },
});
</script>
