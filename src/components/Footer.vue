<template>
  <footer class="footer">
    <input
      type="text"
      class="mess_text"
      placeholder="Написать сообщение..."
      v-model="mess"
      @keydown.enter="sendMess"
    />
    <button class="send__btn" v-if="mess == ''">
      <img src="../assets/img/photo.svg" alt="" @click="modal = true" />
    </button>
    <button class="send__btn" v-else>
      <img src="../assets/img/send.svg" alt="" @click="sendMess" />
    </button>
  </footer>

  <div class="modal" v-if="modal">
    <div class="modal_win">
      <h4 class="modal_title">Отправить картинку</h4>
      <label for="input" class="label">
        <p>URL</p>
        <input type="text" placeholder="URL" v-model="url" />
      </label>
      <label for="input" class="label">
        <p>Комментарий</p>
        <input v-model="mess" type="text" placeholder="Комментарий" />
      </label>
      <div class="modal_btns">
        <button class="modal_btn red" @click="Cancel">Отмена</button>
        <button class="modal_btn" @click="sendPhoto">ОТПРАВИТЬ</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      mess: "",
      modal: false,
      url: '',
    };
  },
  methods: {
    sendMess() {
       const time = `${new Date().getHours()} : ${new Date().getMinutes()}`
      const oneMess = {
        id: this.UserId,
        text: this.mess,
        date: time ,
        url:'',
      };
      if (this.mess.length > 0) {
             this.$emit("oneMess", oneMess); 
      }
            this.mess = ''
    },
    Cancel() {
      this.modal = false;
      this.mess = "";
      this.url = "";
    },
    sendPhoto() {
      const time = `${new Date().getHours()}:${new Date().getMinutes()}`
      const photoSend = {
        id: this.UserId,
        url: this.url,
        text: this.mess,
        date: time,
      };

      this.$emit("photoMess", photoSend);
    },
  },
  props: {
    UserId: Number,
  },
};
</script>

<style></style>
