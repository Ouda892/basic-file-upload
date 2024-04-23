<script>
import axios from 'axios';
export default  {
  data() {
    return {
      file: null,
      type: 'id_back',
    }
  },
  methods: {
    handleFileChange(event) {
      this.file = event.target.files[0]
    },
    uploadFile() {
      let formData = new FormData();
      formData.append('images', this.file);
      formData.append('type', this.type)

      axios.post('http://localhost:5000/auth/me/kyc', formData, {
        headers: {
          'Authorization': 'Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpZCI6ImVmMDQ2OWJjLTgwZWItNGMzNy1hZGI3LWI1MDlhM2M0ZmNlZCIsImVtYWlsIjoib3VkYS53eWNsaWZmZUBnbWFpbC5jb20iLCJyb2xlcyI6WyJST0xFX1VTRVIiXSwiaWF0IjoxNzEzODU2OTc2LCJleHAiOjE3MTM4NjA1NzZ9.5pVB_zoBqHsY1W3mah89H7a1mL1X2rTGI-H-_4nB83I'
        }
      }).then(response => {
        console.log(response)
      }).catch(error => {
        console.log('Error: ', error)
      })
    }
  }
}
</script>

<template>
  <div>
    <input type="file" @change="handleFileChange" />
    <button @click="uploadFile">Upload</button>
  </div>
</template>

<style scoped>

</style>
