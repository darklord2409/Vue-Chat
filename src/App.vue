<template>
  <div class="wrapper">
    <div class="chats">
      <div class="chat">
        <Header :UserId="1" />
        <Main :UserId="1" :messages="messages" />
        <Footer :UserId="1" @oneMess="oneMess" @photoMess="photoMess" />
      </div>
      <div class="chat">
        <Header :UserId="2" />
        <Main :UserId="2" :messages="messages" />
        <Footer :UserId="2" @oneMess="oneMess" @photoMess="photoMess" />
      </div>
    </div>
  </div>

  <div class="documentation container" v-if="doc">
    <h1 class="doc__title">
      👌Добро Пожаловать на сайт/чат Суннатиллаева Азизбека👌
    </h1>
    <p class="doc__text">
      ❗❗Этот сайт разработан в учебных и эксперементальных целях целях❗❗
    </p>
    <p class="doc__text">💎В этом сайте можно:</p>
    <p class="doc__text">💎Отправлять сообщения</p>
    <p class="doc__text">
      💎Отправлять картинки вместе с коментариями отправляющего
    </p>
    <p class="doc__text">💎Изменять Никнейм</p>
    <p class="doc__text">💎Изменить аватарку(писать урл картинки с инета)</p>
    <p class="accept">Прочитали ли вы документацию❓</p>
    <button class="accept__btn" @click="doc = false">Да👌</button>
  </div>
</template>

<script>
import Header from "@/components/Header.vue";
import Main from "@/components/main.vue";
import Footer from "@/components/Footer.vue";
export default {
  data() {
    return {
      messages: [],
      doc: false,
    };
  },
  components: {
    Header,
    Main,
    Footer,
  },
  created() {
    this.doc = true
  },
  methods: {
    oneMess(obj) {
      this.messages.push(obj);
    },
    photoMess(ms) {
      this.messages.push(ms);
    },
  },
};
</script>

<style></style>
