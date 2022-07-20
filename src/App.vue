<template>
  <div>{{ message }}</div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      message: ""
    };
  },
  async mounted() {
    const { text } = await (await fetch("/api/message")).json();
    this.message = text;

    let formData = {
      name: 'Eric',
      email: 'eands9@yahoo.com',
      subject: 'This is the Subject Line',
      message: 'This is the message line!!!'
    }

    let xhr = new XMLHttpRequest();
    xhr.open('POST', '/api/sendmail');
    xhr.setRequestHeader('content-type', 'application/json');
    xhr.onload = function(){
        if(xhr.responseText == 'sucess'){
            alert('Email sent');
            name.value = '';
            email.value = '';
            subject.value = '';
            message.value = '';
        }else{
            alert('Something went wrong!')
        }
    }

    xhr.send(JSON.stringify(formData));
  }
};
</script>