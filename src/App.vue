<template>
  <main>
    <div class="form">
      <form id="inputform" name="inputform" method="POST">
        <fieldset>
          <label>Digite seu email</label><br>
          <input type="text" required name="email" id="email" v-model="form.email" :key="email"><br>
          <label>Digite sua senha</label><br>
          <input type="text"  required name="senha" id="senha" v-model="form.senha" :key="senha"  ><br>
          <button @click="postForm()">Enviar</button>
        </fieldset>
      </form>
    </div>
  </main>
</template>
<script>
const axios = require('axios').default;
export default{
  name: 'App',
  data(){
    return{
      form:{
        email: '',
        senha: ''
      },
    }
  },
  methods:{
    postForm(){
                let form = document.querySelector('#inputform');
                axios.post('http://localhost/novologin/novoLogin.php', form)
                .then(response => {
                alert(response.data) ;
                if(response.data == 'logado'){
                  window.location.href='https://www.google.com/webhp?hl=pt-BR&sa=X&ved=0ahUKEwiV5d7_yrT-AhUWDrkGHbQXBDMQPAgI';
                }else{
                  window.location.href='http://localhost:8080/';
                }
                
                })
                .catch(error => error)
            },
    }
  }

</script>
<style>
.form{
  display: flex;
  position: absolute;
  background-color: rgb(131, 88, 127);
  padding: 15px;
  border-radius: 15px;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  
}
.form input{
  background-color: chartreuse;
}

@media screen and (max-width: 372px) {
    .form{
        display: block;
    }
  }
</style>