<template>
    <div class="container">
      <h2 class="mt-4 mb-3">Thêm mới Liên hệ</h2>
      <div class="row">
        <div class="col-md-6">
          <form @submit.prevent="addContact" class="form">
            <div class="form-group">
              <label for="name">Tên:</label>
              <input type="text" id="name" v-model="contact.name" class="form-control" required>
            </div>
            <div class="form-group">
              <label for="email">Email:</label>
              <input type="email" id="email" v-model="contact.email" class="form-control" required>
            </div>
            <div class="form-group">
              <label for="phone">Số điện thoại:</label>
              <input type="tel" id="phone" v-model="contact.phone" class="form-control" required>
            </div>
            <div class="form-group">
              <label for="address">Địa chỉ:</label>
              <textarea id="address" v-model="contact.address" class="form-control"></textarea>
            </div>
            <button type="submit" class="btn btn-primary">Lưu</button>
          </form>
        </div>
      </div>
    </div>
  </template>
  
  <script>
  import ContactService from "@/services/contact.service";
  
  export default {
    data() {
      return {
        contact: {
          name: '',
          email: '',
          phone: '',
          address: ''
        }
      };
    },
    methods: {
      async addContact() {
        try {
          await ContactService.create(this.contact);
          alert('Thêm mới Liên hệ thành công!');
          this.$router.push({ name: 'contactbook' });
        } catch (error) {
          console.error(error);
          alert('Đã xảy ra lỗi khi thêm mới Liên hệ.');
        }
      }
    }
  };
  </script>
  
  <style scoped>
  .container {
    max-width: 600px;
    margin: auto;
  }
  
  .form {
    padding: 20px;
    border: 1px solid #ccc;
    border-radius: 5px;
    background-color: #f9f9f9;
  }
  
  .form-group {
    margin-bottom: 20px;
  }
  
  label {
    font-weight: bold;
  }
  
  .btn-primary {
    background-color: #007bff;
    border-color: #007bff;
  }
  </style>
  