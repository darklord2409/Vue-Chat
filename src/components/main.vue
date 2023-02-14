<template>
  <main class="main">
    <div class="messages" v-for="masses in messages" :key="masses.date">
      <div
        class="message"
        :class="{
          left: UserId != masses.id,
        }"
      >
        <p class="message_date">{{ masses.date }}</p>

        <div class="message_text">
         
            <img
              class="chats_img"
              :src="masses.url"
              :class="{none: masses.url!=''}"
            />
            <p> {{ masses.text }} </p>
        </div>
      </div>
    </div>
  </main>
</template>

<script>
export default {
  data() {
    return {};
  },
  props: {
    UserId: Number,
    messages: Array,
  },
};
</script>

<style></style>
