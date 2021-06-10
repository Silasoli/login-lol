<template>
  <div class="home">
    <div id="login">
     <div id="login-form">
       <div id="fields">
         <h1 id="title-fields">Bem vindos a League of Draven</h1>
         <v-form>
           <v-text-field v-model="nickname" label="Nickname"  required></v-text-field>
           <v-text-field type="password"  v-model="senha" label="Senha" required></v-text-field>
         </v-form>
        <v-btn id="go-cad-btn" class="ma-2"
        outlined
        color="indigo" @click="goLogin">Logar</v-btn>
       </div>
     </div>
      <div id="main">
        <div id="top-table">
           <h1>Bem vindo(a), {{usuLogado}}</h1>
        </div>
        <div id="table" class="classMain">
          <v-simple-table height="200px">
            <template v-slot:default>
              <thead>
                <tr>
                  <th class="text-left">
                    Name
                  </th>
                  <th class="text-left">
                    Maestria
                  </th>
                </tr>
              </thead>
               <tbody>
                <tr
                  v-for="item in desserts"
                  :key="item.name">
                  <td>{{ item.name }}</td>
                  <td>{{ item.maestria }}</td>
                </tr>
              </tbody>
            </template>
          </v-simple-table>
        </div>
        <div id="bottom-table" class="classMain">
          <v-btn id="go-cad-btn" class="ma-2"
           outlined
           color="indigo" @click="logout">Sair</v-btn>
        </div>
     </div>
  </div>
  </div>  
</template>

<script>
export default {
  name: 'home',
   mounted() {
      
  },
  data(){
    return{
    nickname: '',
    senha: '',
    usuLogado:localStorage.getItem('user'),
        desserts: [
          {
            name: 'Irelia',
            maestria: '201.425'
          },
          {
            name: 'Leona',
            maestria: '156.298',
          },
          {
            name: 'Thresh',
            maestria: '124.217',
          },
            {
            name: 'Lux',
            maestria: '120.708',
          },
          {
            name: 'Zyra',
            maestria: '102.878',
          },
          {
            name: 'Braum',
            maestria: '95.183',
          },
        ],
  }
  },
  components: {
  },
  methods:{
  goLogin: function(){
    var nickUsu = this.nickname;
    var senhaUsu = this.senha;
    if(nickUsu==''){
    this.$swal('Preencha o campo "Nickname"')
    }else if(nickUsu.length<6||nickUsu.length>7){
      this.$swal('Nickname invalido')
    }else{
       if(senhaUsu==''){
        this.$swal('Preencha o campo "Senha"')
       }else if(senhaUsu.length<6){
        this.$swal('Senha Invalida')
       } else{
         localStorage.setItem('user', nickUsu);
         document.getElementById('login-form').classList.add("hideOn");
         document.getElementById('main').classList.add("hideOff");
         setTimeout(() => {
            this.$swal('logado com sucesso')
         }, 2300);
         this.getName();
       }
    }
  },
  logout: function(){
    localStorage.clear();
    document.location.reload(true);
   },
   getName: function(){
     this.usuLogado = localStorage.getItem('user');
   }
  }
}
</script>
<style scoped>
#login{
  background-image: url("http://www.alollover.com/wp-content/uploads/2020/09/Vayne_15FPX-Vayne.jpg");
  background-size:cover;
  position: fixed;
  top: 50%;
  left: 50%;
  -webkit-transform: translate(-50%, -50%);
  transform: translate(-50%, -50%);
  width: 75%;
  height: 72%;
  -webkit-box-shadow: 0 0 20px gray;
  box-shadow: 0 0 20px gray;
  border-radius: 10px;
}

#login-form{
  float: left;
  background-color: #DCDCDC	;
  width: 65%;
  height: 100%;
  border-top-left-radius: 10px;
  border-bottom-left-radius: 10px;
}

#fields{
  width: 50%;
  position: fixed;
  top: 50%;
  left: 32%;
  -webkit-transform: translate(-50%, -50%);
  transform: translate(-50%, -50%);
}
#title-fields{
  text-align: center;
  margin-bottom: 40px;
  font-size: 1.6em;
}
#go-cad-btn{
 width: 100%;
 color:black !important;
 padding: 2vw;
 margin: 0px !important;
}
#go-cad-btn:hover{
  background-color: black;
  color:white !important;
}

#main{
  float: right;
  background-color: #DCDCDC;
  width: 65%;
  height: 100%;
  border-top-right-radius: 10px;
  border-bottom-right-radius: 10px;
  position: absolute;
  right: 0px;
  top: 0px;
  opacity: 0%;
}
.hideOff{
  opacity: 100% !important;
  transition-property: opacity;
  transition-duration: 4s;
}
.hideOn{
  opacity: 0;
  transition-property: opacity;
  transition-duration: 2s;
}
.classMain{
  margin-top: 4vw;
  margin-left: 2vw;
  margin-right: 2vw;
  width: 44vw;
}
#table{
  font-size: 1.6em;
 -webkit-box-shadow: 0 0 20px gray;
  box-shadow: 0 0 20px gray;
}
#top-table{
  margin-top: 2vw;
  margin-left: 2vw;
  margin-right: 2vw;
  width: 44vw
}
#bottom-table{
  margin-top: 1vw !important;
}
</style>
