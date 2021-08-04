<template>


<div class="main">
  <div class="container">
    <div class="row">
      <div class="col-4">
        <div class="left">
              <div class="inserted-upload">
                <button class='upload-button' @click="generate">Загрузить нового пользователя</button>
                <p>Имя пользователя</p>
                <p>{{Namebuf}}</p>
                <p>Почта</p>
                <p>{{Mailbuf}}</p>
                <p>Телефон</p>
                <p>{{PhoneBuf}}</p>
                <p>Сайт</p>
                <p>{{SiteBuf}}</p>

              </div>
        </div>
      </div>
      <div class="col-8 right">
        <div class="col tt t-1">
              <div class="tokens">
                Вставить токен
                <input @click="insert('name')" type="button" value="Имя">
                <input @click="insert('mail')" type="button" value="Почта">
                <input @click="insert('phone')" type="button" value="Телефон">
                <input @click="insert('site')" type="button" value="Сайт"> 
              </div>
        </div>
        <div class="col tt t-2">
          <textarea v-model="current_input"></textarea>
        </div>
        <div class="col tt t-3">
                <div class="tokens">
                  Вставить токен
                  <input  type="button" value="Загрузить из LocalStorage">
                  <input  type="button" value="Загрузить в LocalStorage">
  
              </div>
        </div>
        <div class="col tt t-4">
          {{this.current_input}}
        </div>
      </div>
    </div>
  </div>
 

  <!--<div class="left-upload">

  </div>
  <div class="right-field">

    <div style="padding:5px;" class='input-text'>
      <textarea
      v-model="current_input"
      type="textarea" style="rows=4;width:98%;margin:1%;">

      </textarea>
    </div>
    <div class="local"></div>
    <div class="results">{{this.current_input}}</div>
  </div> -->
</div>


</template>

<script>



export default {
  name: 'App',
  components: {
    
    
  },

  data(){
      return {

      current_input : ' ',
      
      Name : ['Sergey', 'Vladilen', 'Ilya', 'Mareyn', 'Atraxa', 'Yarok'],
      Mail : ['kfc@mail.ru', 'noizemc@mail.ru','thirdemail@mail.ru','helloworld@mail.ru', 'b.ada@mail.ru'],
      Phone : ['1232','4352','4357','0536'],
      Site : ['1232.com','4352.com','4357.com','0536.com'],

      Namebuf : '',
      Mailbuf : '',
      PhoneBuf : '',
      SiteBuf : ''
      }
  },

  mounted: function(){
    this.generate();
  },

  methods:{
    generate(){
       this.Namebuf = '<<' + this.arrayRandElement(this.Name) + '>>';
       this.Mailbuf = '<<' + this.arrayRandElement(this.Mail) + '>>';
       this.PhoneBuf = '<<' + this.arrayRandElement(this.Phone) + '>>';
       this.SiteBuf = '<<' + this.arrayRandElement(this.Site) + '>>';
    },

    arrayRandElement(arr){
      var rand = Math.floor(Math.random() * arr.length);
      return arr[rand];
    },


    insert(value){
      if (value == 'name'){
        this.current_input+=this.Namebuf;
      }
      if (value == 'mail'){
        this.current_input+=this.Mailbuf;
      }
      if (value == 'phone'){
        this.current_input+=this.PhoneBuf;
      }
      if (value == 'site'){
        this.current_input+=this.SiteBuf;
      }
    },
  },
}
</script>



<style>

@import url('https://fonts.googleapis.com/css2?family=Jura:wght@700&display=swap');
@import url("https://cdn.jsdelivr.net/npm/bootstrap@5.0.2/dist/css/bootstrap.min.css");


.header {
  margin-bottom: 80px;
}


.main {
  font-family: 'Jura', sans-serif;
  color: aliceblue;
  min-height: 300px;
  margin-top: 50px;
}

.train {
  padding: 20px;

  background-color: rgb(138, 138, 138);
  position: relative;
  border: rgb(255, 255, 255) 1px solid;
}

.left {
  height: 400px;
}

.right {
  background-color: rgb(42, 40, 40);
  padding: 20px;
  border-radius: 30px;
  overflow: hidden;
  padding-right: 20px;
}

.t-1 { 
  height: 100px;
  background-color: rgb(107, 107, 107);
}

.t-2, .t-4 {
  height: 180px;
  background-color: rgb(170, 170, 170);
}

.t-3 {
  height: fit-content;
  background-color: rgb(107, 107, 107);
}
.tt {
  margin-bottom: 20px;
  border-radius: 10px;
  padding: 10px;

}

.inserted-upload{
  padding: 30px;
  background-color: rgb(63, 63, 52);
  height: auto;
 

  width: auto;
  border-radius: 30px;
}

.upload-button{
    min-width: fit-content;
    background-color: #4CAF50; /* Green */
    border: none;
    font-family: 'Jura', sans-serif;
    color: white;
    padding: 15px 32px;
    text-align: center;
    text-decoration: none;
    display: inline-block;
    font-size: 16px;
}
.upload-button:hover{
    background-color: #126415; /* Green */
    color: white;
}
.upload-button:active{
    background-color: rgb(158, 172, 156); /* Green */
    color: black;
}

.left-upload {

  float: left;
  padding: 10px;
 /* margin: 5px;
  width: 30%;
  height: 500px;
  background-color: #2c3e50;
  border: 10px green solid;
  */
  display: inline-block;
}

.right-field {
  
  display: inline-block;
  
  width: 60%;
  margin: 5px;
  height: fit-content;
  margin-top:12px;
  padding: 10px;
  background-color: #2c3e50;
  
}


  .tokens{
    margin-bottom: 12px;
  }
  .input-text{
    background-color: rgb(33, 90, 7);
  }

  textarea{
    width:100%;
    resize: none;
    color: white;
    height: 100%;
    background-color:  rgb(187, 187, 187);
    border:2px solid #aaa;
    border-radius:7px;
    overflow: hidden;
    margin: 0;
    outline:none;
    padding:8px;
    box-sizing: border-box;
  }
  input[type=text]:focus{
    border-color:dodgerBlue;
    box-shadow:0 0 8px 0 dodgerBlue;
  }

input[type=button]{
    width:fit-content;
    background-color : #4CAF50;
    color: seashell;
    margin-left: 5px;
    padding: 10px 20px;
    border: none;
    margin-top: 12px;
  }

  input[type=button]:hover{
    background-color: #126415; /* Green */
    color: white;
  }

  input[type=button]:active{
      background-color: rgb(158, 172, 156); /* Green */
      color: black;
  }



  .local {
    height: 60px;
    background-color: rgb(98, 133, 82);
  }
  .results {
    min-height: 60px;
    height: fit-content;
    padding-bottom: 10px;
    background-color: rgb(33, 90, 7);
  }

  body {
    margin: 0px;
    background-color: rgb(241, 241, 241);
  }

</style>
