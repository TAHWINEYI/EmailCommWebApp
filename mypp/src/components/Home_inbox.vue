<template>
  <div class="container-fluid h-100">
    <div class="row h-100">
      <div class="col-2 bg-light border-end p-0">
        <div class="d-flex flex-column h-100">
          <div class="p-3 border-bottom flex-grow-1">
            <button class="btn btn-success w-100" @click="showComposeModal = true">
              <i class="bi bi-plus-circle"></i> Compose email
            </button>
          </div>
          <div class="flex-grow-1">
            <div class="list-group list-group-flush">
              <a href="#" class="list-group-item list-group-item-action" :class="{ 'active': currentTab === 'inbox' }" @click.prevent="currentTab = 'inbox'" @click="showMaiList = true">
                <i class="bi bi-inbox"></i> Inbox
              </a>
              <a href="#" class="list-group-item list-group-item-action" :class="{ 'active': currentTab === 'sent' }" @click.prevent="currentTab = 'sent'">
                <i class="bi bi-send"></i> Sent
              </a>
              <a href="#" class="list-group-item list-group-item-action" :class="{ 'active': currentTab === 'drafts' }" @click.prevent="currentTab = 'drafts'">
                <i class="bi bi-file-earmark"></i> Drafts
              </a>
              <a href="#" class="list-group-item list-group-item-action" :class="{ 'active': currentTab === 'outbox' }" @click.prevent="currentTab = 'outbox'">
                <i class="bi bi-file-earmark"></i> Outbox
              </a>
               
            </div>
           
          </div>
        </div>
        <div>
            <button href="#" class="btn btn-warning w-100" :class="{ 'active': currentTab === 'logout' }" @click.prevent="currentTab = 'logout'">
            <i class="bi bi-file-earmark"></i> Logout</button>
        </div>
      </div>
      <div class="col-10 p-0">
        <div class="d-flex flex-column h-100">
          <div class="border-bottom p-3">
            <div class="input-group d-flex" >
              <input type="text" class="form-control flex-grow-1" style="width:70%" placeholder="Search mail" v-model="searchQuery">
              <button class="btn btn-primary flex-grow-2" style="width:20%" type="button">
                <i class="bi bi-search"> Search</i>
              </button>
            </div>
          </div>
          <div class="flex-grow-1 overflow-auto">
            <div v-if="currentTab === 'inbox'">
              <MailList :mails="inboxMails" />
            </div>
            <div v-else-if="currentTab === 'sent'">
              <MailList :mails="sentMails" />
            </div>
            <div v-else-if="currentTab === 'drafts'">
              <MailList :mails="draftMails" />
            </div>
          </div>
        </div>
      </div>
    </div>

   <div v-if="showComposeModal" class="modal fade show" tabindex="-1" role="dialog" style="display: block; background-color: rgba(0, 0, 0, 0.5);">
      <div class="modal-dialog modal-dialog-centered modal-lg" role="document">
        <div class="modal-content">
          <div class="modal-header">
            <h5 class="modal-title">Compose New Email</h5>
            <button type="button" class="btn-close" @click.prevent="showComposeModal = false"></button>
          </div>
          <div class="modal-body">
            <ComposeForm @send-mail="sendMail" @close-modal="showComposeModal = false" />
          </div>
        </div>
      </div>
    </div>
  
  </div>

</template>

<script>
import MailList from '@/components/MailList.vue'
import ComposeForm from '@/components/ComposeForm.vue'

export default {
  name: 'EmailApp',
  components: {
   MailList,
   ComposeForm
  },
  data() {
    return {
      currentTab: 'inbox',
      searchQuery: '',
      showComposeModal: false,
      inboxMails: [
        // Sample inbox mails data
        { id: 1, from: 'john@example.com', subject: 'Meeting update', date: '2023-05-25' },
        { id: 2, from: 'jane@example.com', subject: 'New project proposal', date: '2023-05-24' },
        { id: 3, from: 'bob@example.com', subject: 'Follow up on task', date: '2023-05-23' }
      ],
      sentMails: [
        // Sample sent mails data
        { id: 1, to: 'alice@example.com', subject: 'Presentation slides', date: '2023-05-22' },
        { id: 2, to: 'tom@example.com', subject: 'Invoice for last month', date: '2023-05-21' },
        { id: 3, to: 'sara@example.com', subject: 'Feedback on the report', date: '2023-05-20' }
      ],
      draftMails: [
        // Sample draft mails data
        { id: 1, to: 'david@example.com', subject: 'Meeting agenda', date: '2023-05-19' },
        { id: 2, to: 'emily@example.com', subject: 'Project update', date: '2023-05-18' },
        { id: 3, to: 'michael@example.com', subject: 'Discuss new initiative', date: '2023-05-17' }
      ]
    }
  },
  methods: {
    sendMail(newMail) {
      // Add the new mail to the appropriate list (inbox, sent, or drafts)
      console.log('New mail sent:', newMail);
      this.showComposeModal = false;
    }
  }
}
</script>

<style scoped>
.h-100 {
  height: 100vh;
}
</style>