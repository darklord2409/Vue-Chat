<template>
  <header class="header">
    <div class="prof_avas">
       <img :src="avatarka[UserId]" alt="" class="pof_ava" />
    <button class="pen_btn"><i class="fas pen" @click="modalAva = true"></i></button>
    </div>
   
    <div class="info">
      <h3 class="user__name">{{ profiles[UserId].name }}</h3>
      <p class="user_status">online</p>
    </div>
    <button class="options" @click="modals"><i class="fas gear"></i></button>
  </header>


  <div class="modal_name" v-if="modalAva  || modal" @click="closeModal">
    <label for="" class="modal_options">
      <h5 class="opyions_title">Изменить {{modal ? 'имя' : 'аватарку'}}</h5>
      <input type="text" class="options_input" @keydown.enter="AddName" v-model="NewName" />
      <button class="options_btn" @click="AddName" >Изменить</button>
    </label>
  </div>
</template>

<script>
export default {
  data() {
    return {
      modal: false,
      modalAva: false,
      NewName:'',
      avatarka: {
        1: require("../assets/img/ava1.svg"),
        2: require("../assets/img/ava2.svg"),
      },
      profiles: {
        1 : { name: "Evgeniy" },
        2 : { name: "Aziz" }  
      },
    };
  },
  methods: {
    modals() {
      this.modal = !this.modal;
    },
    closeModal(e) {
      let closeTarget = e.target.getAttribute('class');
      if (closeTarget == 'modal_name') {
        this.modal = false
        this.modalAva = false
      }
    },
    AddName(){
      if (this.NewName != '' && this.modal == true) {
         this.profiles[this.UserId].name = this.NewName
               this.modal = false
      }else if (this.NewName != '' && this.modalAva == true) {
         this.avatarka[this.UserId] = this.NewName
          this.modalAva = false
      }
      this.NewName = ''
     
    },
    // options(id){
        
    // }
  },
  props: {
    UserId: Number,
    userName: String,
  },
};
</script>

<style></style>
