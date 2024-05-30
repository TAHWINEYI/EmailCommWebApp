<template>
    <div class="container my-5">
      <table class="table table-striped table-hover">
        <tbody>
          <tr v-for="email in emails" :key="email.id">
            <td>{{ email.from }}</td>
            <td>{{ email.subject }}</td>
            <td>{{ email.date }}</td>
            <td>
              <button class="btn btn-primary btn-sm mr-2" @click="replyToEmail(email)">Reply</button>
              <button class="btn btn-danger btn-sm" @click="deleteEmail(email)">Delete</button>
            </td>
          </tr>
        </tbody>
      </table>
    </div>
  </template>
  
  <script>
  export default {
    data() {
      return {
        emails: [
          {
            id: 1,
            from: 'john@example.com',
            subject: 'Meeting agenda',
            date: '2023-05-27',
          },
          {
            id: 2,
            from: 'jane@example.com',
            subject: 'Upcoming project',
            date: '2023-05-26',
          },
          {
            id: 3,
            from: 'bob@example.com',
            subject: 'Feedback on report',
            date: '2023-05-25',
          },
        ],
      };
    },
    methods: {
      replyToEmail(email) {
        // Implement email reply functionality
        console.log(`Replying to email from ${email.from}`);
      },
      deleteEmail(email) {
        // Implement email deletion functionality
        console.log(`Deleting email from ${email.from}`);
      },
    },
  };
  </script>