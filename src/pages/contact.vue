<template>
  <Layout>
    <div  class="container">
      <div  class="contact-header">
        <h1  class="contact-title">Say hi!</h1>
        <p >
          Leave me a note with any questions you might have, I'll get back to
          you as soon as possible.
        </p>
      </div>
      <form  name="contact" class="contact-form" @submit.prevent="onSubmit()">
        <div  class="sender-info">
          <div >
            <label  for="name"  class="label">Your name</label
            ><input v-model="form.name" required type="text" name="name" />
          </div>
          <div >
            <label  for="email" class="label"
              >Your email</label
            ><input v-model="form.email" required type="email" name="email" />
          </div>
        </div>
        <div  class="message">
          <label  for="message"
                  class="label">Message</label
          ><textarea v-model="form.message" required name="message"></textarea>
        </div>
        <button  class="button"
                 type="submit"

        >Submit form</button>
      </form>
    </div>
  </Layout>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      form: {
        name: "",
        email: "",
        message: "",
      },
    };
  },
  methods: {
    onSubmit() {
      axios.post(this.GRIDSOME_API_URL+'/contacts',{
        ...this.form
      }).then((res)=>{
        console.log()
        if(res.data){
          alert('成功！')
          this.form={
            name: "",
            email: "",
            message: "",
          }
        }else{
          alert('失败，请填写完整')
        }


      })
    },
  },
};
</script>

<style>
</style>