<template>


<div class="main">
  <div class="container">
    <div class="row gy-5">
      <div class="col-lg-4 col-md-5">
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
                <p>&lt;&lt;{{SiteBuf}}&gt;&gt;</p>
              </div>
        </div>
      </div>
      <div class="col-lg-8 col-md-7 right">
        <div class="col tt t-1">
              <div class="row">
                <div class="col-12 col-md-12 col-lg-2 tokens"> Вставить токен 
                  
                </div>
                <div class="col-10">
                  <input @click="insert('name')" type="button" value="Имя">
                  <input @click="insert('mail')" type="button" value="Почта">
                  <input @click="insert('phone')" type="button" value="Телефон">
                  <input @click="insert('site')" type="button" value="Сайт"> 
                </div>
              </div>
      
        </div>
        <div class="col tt t-2">
          <textarea v-model="current_input" v-html="current_input_html"></textarea>
        </div>
        <div class="col tt t-3">
                <div class="tokens">
                    <input @click="uploadFromLS" type="button" value="Загрузить из LocalStorage">
                    <input @click="uploadToLS" type="button" value="Загрузить в LocalStorage">
                </div>
        </div>
        <div class="col tt t-4" v-html="this.current_input_html">
      
        </div>
      </div>
    </div>
  </div>
</div>


</template>

<script>



export default {
  name: 'App',
  components: {
    
    
  },

  data(){
      return {

      current_input : '',
      current_input_html : '',

    

      Name : ['Sergey', 'Vladilen', 'Ilya', 'Mareyn', 'Nikita', 'Darya'],
      Mail : ['kfc@mail.ru', 'randommail@mail.ru','thirdemail@mail.ru','helloworld@mail.ru', 'b.ada@mail.ru'],
      Phone : ['+7(123)221-21-45','+4(352)454-23-67','+8(357)432-73-90','+1(536)003-34-18'],
      Site : ['google.com','yandex.com','vk.com','youtube.com'],

      Namebuf : '',
      Mailbuf : '',
      PhoneBuf : '',
      SiteBuf : ''
      }
  },

  mounted: function(){
    this.generate();
  },


  watch : {
    current_input(){
      let buffer = this.current_input.replaceAll('<S<', `<a class='TOKEN SITE' target='_blank' href=${'https://'+this.SiteBuf}>`);
      buffer = buffer.replaceAll('>S>', "</a>");

      buffer = buffer.replaceAll('<<', "<div class='TOKEN'>");
      buffer = buffer.replaceAll('>>', "</div>");

      this.current_input_html = buffer;
    }
  },

  methods:{

    uploadToLS(){
      localStorage.setItem('current_input', this.current_input);
    },

    uploadFromLS(){
      this.current_input = localStorage.getItem('current_input');
    },

    generate(){
       this.Namebuf = '<<' + this.arrayRandElement(this.Name) + '>>';
       this.Mailbuf = '<<' + this.arrayRandElement(this.Mail) + '>>';
       this.PhoneBuf = '<<' + this.arrayRandElement(this.Phone) + '>>';
       this.SiteBuf = this.arrayRandElement(this.Site);
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
        this.current_input+=('<S<' +this.SiteBuf + '>S>');
      }
    },
  },
}
</script>



<style>

@import url('https://fonts.googleapis.com/css2?family=Jura:wght@700&display=swap');
@import url("https://cdn.jsdelivr.net/npm/bootstrap@5.0.2/dist/css/bootstrap.min.css");

  @media (max-width : 992px) {
     .t-1 {
         height: 150px;
      }
      input[type=button] {
        padding: 12px;
      }
  }


    @media (max-width : 768px) {
     .t-1 {
         height: 110px;
      }
  }



      @media (max-width : 416px) {
     .t-1 {
         height: 170px;
      }
  }



</style>


