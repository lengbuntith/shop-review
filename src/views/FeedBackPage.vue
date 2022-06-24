<template>
  <div style="background-color: red; height: 100%;">
    <header-2 />
    <section class="py-5 my-5">
      <div class="container">
        <h1 class="mb-5">Feedback</h1>
        <div class="bg-white shadow rounded-lg d-block d-sm-flex">
          <div class="tab-content p-4 p-md-5" id="v-pills-tabContent">
            <div
              class="tab-pane fade show active"
              id="account"
              role="tabpanel"
              aria-labelledby="account-tab"
            >
              <h3 class="mb-4">Feedback Form</h3>
              <div class="row">
                <div class="col-md-6">
                  <div class="form-group">
                    <label>First Name</label>
                    <input type="text" class="form-control" value="" />
                  </div>
                </div>
                <div class="col-md-6">
                  <div class="form-group">
                    <label>Last Name</label>
                    <input type="text" class="form-control" value="" />
                  </div>
                </div>
                <div class="col-md-6">
                  <div class="form-group">
                    <label>Email</label>
                    <input type="text" class="form-control" value="" />
                  </div>
                </div>
                <div class="col-md-6">
                  <div class="form-group">
                    <label>Subject</label>
                    <input type="text" class="form-control" value="" />
                  </div>
                </div>
                <div class="col-md-12">
                  <div class="form-group">
                    <label>Message</label>
                    <textarea class="form-control" rows="4"></textarea>
                  </div>
                </div>
              </div>
              <div>
                <button class="btn btn-primary" @click="submit">Submit</button>
                <button class="btn btn-light">Cancel</button>
              </div>
            </div>
          </div>
        </div>
      </div>
    </section>
  </div>
</template>

<script>
import Header2 from '../components/Header2.vue'

export default {
  components: { Header2 },
  name: 'EditProfile',
  methods: {
    async submit(){
         const post_submit = await fetch('http://localhost:3001/post/create', {
        method: 'POST',
        credentials: 'include',
        headers: {
          'Content-type': 'application/json',
        },
        body: JSON.stringify({
          firstName: this.firstName,
          lastName: this.lastName,
          email: this.email,
          subject: this.subject,
          message: this.message
        })
      })
       alert('Message sent successfully~')
        this.$router.push('/')
    }
  },
  mounted() {

  },
}
</script>

<style scoped>
.container {
  position: fixed;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}
</style>
