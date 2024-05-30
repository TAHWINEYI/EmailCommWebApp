<template>
     <h8 class="alert alert-primary d-flex justify-content-left" style="text-center">FREE-MAIL C0MPOSE</h8>
    <div class="email-composer">
      <form @submit.prevent="sendEmail">
        <div class="form-group d-flex">
          <label class="flex-grow-1" style="width: 20%;" for="to">To:</label>
          <input  class="flex-grow-1" style="width: 80%;" type="email" id="to" v-model="email.to" required />
        </div>
  
        <div class="form-group d-flex">
          <label class="flex-grow-1" style="width: 20%;" for="cc">CC:</label>
          <input class="flex-grow-1" style="width: 80%;" type="email" id="cc" v-model="email.cc" />
        </div>
  
        <div class="form-group d-flex">
          <label class="flex-grow-1" style="width: 20%;" for="subject">Subject:</label>
          <input class="flex-grow-1" style="width: 80%;" type="text" id="subject" v-model="email.subject" required />
        </div>
  
        <div class="form-group d-flex">
          <label class="flex-grow-1" style="width: 20%;" for="content">Message:</label>
          <textarea class="flex-grow-1" style="width: 80%;" id="content" v-model="email.content" required></textarea>
        </div>
  
        <div class="form-group d-flex">
          <label for="attachments" class="flex-grow-1" style="width: 20%;"> Attachments:</label>
          <input class="flex-grow-1" style="width: 80%;" type="file" id="attachments" ref="attachments" multiple @change="handleAttachmentUpload" />
          <div class="attached-file"  v-if="email.attachments.length > 0">
            <div v-for="(attachment, index) in email.attachments" :key="index">
              <span>{{ attachment.name }}</span>
              <button @click.prevent="removeAttachment(index)">Remove</button>
            </div>
          </div>
        </div>
  
        <div class="form-group">
          <button type="submit" :disabled="isSending">
            <span v-if="isSending">Sending...</span>
            <span v-else>Send</span>
          </button>
          <button type="button" @click="saveAsDraft">Save as Draft</button>
        </div>
      </form>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        email: {
          to: '',
          cc: '',
          bcc: '',
          subject: '',
          content: '',
          attachments: [],
        },
        isSending: false,
      };
    },
    methods: {
      handleAttachmentUpload(event) {
        this.email.attachments = [...event.target.files];
      },
      removeAttachment(index) {
        this.email.attachments.splice(index, 1);
      },
      sendEmail() {
        this.isSending = true;
        // Implement email sending logic here
        // ...
        this.isSending = false;
        this.resetForm();
      },
      saveAsDraft() {
        // Implement saving email as draft logic here
        // ...
        this.resetForm();
      },
      resetForm() {
        this.email = {
          to: '',
          cc: '',
          bcc: '',
          subject: '',
          content: '',
          attachments: [],
        };
      },
    },
  };
  </script>
  
  <style scoped>
  .email-composer {
    max-width: 800px;
    margin: 0 auto;
    padding: 2rem;
  }
  
  .form-group {
    margin-bottom: 1.5rem;
  }
  
  label {
    display: block;
    font-weight: bold;
    margin-bottom: 0.5rem;
  }
  
  input,
  textarea {
    width: 100%;
    padding: 0.5rem;
    font-size: 1rem;
    border: 1px solid #ccc;
    border-radius: 4px;
  }
  
  .attached-files {
    margin-top: 0.5rem;
  }
  
  .attached-files > div {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-bottom: 0.5rem;
  }
  
  button {
    padding: 0.5rem 1rem;
    font-size: 1rem;
    background-color: #007bff;
    color: #fff;
    border: none;
    border-radius: 4px;
    cursor: pointer;
  }
  
  button:disabled {
    background-color: #ccc;
    cursor: not-allowed;
  }
  
  button + button {
    margin-left: 0.5rem;
  }
  </style>


