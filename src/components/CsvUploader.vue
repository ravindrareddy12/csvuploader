<!-- components/CsvUpload.vue -->

<template>
  <div>
    <input type="file" @change="handleFileUpload" />
    <button @click="uploadFile">Upload CSV</button>
  </div>
</template>

<script>
import axios from 'axios';
export default {
  
  data() {
    return {
      selectedFile: null,
    };
  },
  methods: {
    handleFileUpload(event) {
      this.selectedFile = event.target.files[0];
    },
    
    uploadFile() {
      const formData = new FormData();
      formData.append('csvFile', this.selectedFile);


      // Send the CSV file to the Laravel backend using Axios
      axios.post('http://127.0.0.1:8000/api/upload-csv', formData, {
        headers: {
          'Content-Type': 'multipart/form-data',
        },
      })
      .then(response => {
        console.log(response.data);

      })
      .catch(error => {
        console.error(error);
      });
    },
  },
};
</script>


