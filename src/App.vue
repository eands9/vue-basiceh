<template>
  <div>{{ message }}</div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      message: "",
      email: "",
      subject: "",
      name: "",
      formData: "test"
    };
  },
  async mounted() {
    // const { text } = await (await fetch("/api/message")).json();
    // this.message = text;

    // const formData = {
    //   this.name: 'Eric',
    //   this.email: 'eands9@yahoo.com',
    //   this.subject: 'This is the Subject Line',
    //   this.message: 'This is the message line!!!'
    // }

    let xhr = new XMLHttpRequest();
    // xhr.open('POST', '/api/sendmail');
    xhr.open('POST', '/api/sendmail');
    xhr.setRequestHeader('content-type', 'application/json');
    xhr.onload = function(){
        if(xhr.responseText == 'sucess'){
            alert('Email sent');
            this.name.value = '';
            this.email.value = '';
            this.subject.value = '';
            this.message.value = '';
        }else{
            alert('Something went wrong!')
        }
    }

    xhr.send(JSON.stringify(this.formData));
  }
};
</script>