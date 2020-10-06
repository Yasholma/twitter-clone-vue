<template>
  <div class="tweet" @click="favTweet(tweet.id)">
    <h4 class="tweet__user">@{{ username }}</h4>
    <p class="tweet__content">{{ tweet.content }}</p>
    <p class="tweet__like">
      <span class="tweet__like__count"> {{ tweet.likes }}</span> Likes
    </p>
  </div>
</template>

<script>
export default {
  props: {
    username: {
      type: String,
      required: true,
    },
    tweet: {
      type: Object,
      required: true,
    },
  },

  methods: {
    favTweet(id) {
      this.$emit("fav-tweet", id);
    },
  },
};
</script>

<style>
.tweet {
  background: #fff;
  padding: 1rem;
  margin: 0;
  margin-bottom: 1rem;
  border-radius: 0.3rem;
  cursor: pointer;
  transition: 0.3s ease-in;
  border-top: 6px solid purple;
}

.tweet:hover {
  transform: translateX(5px) scale(1.02);
}

.tweet__user {
  margin: 0;
  font-family: cursive;
  font-size: 1.8rem;
}

.tweet__content {
  margin-top: 0;
  line-height: 1.5;
  font-family: "Segoe UI", Tahoma, Geneva, Verdana, sans-serif;
}

.tweet__like {
  display: flex;
  align-items: center;
}

.tweet__like__count {
  width: 20px;
  height: 20px;
  background: rebeccapurple;
  border-radius: 50%;
  display: grid;
  place-content: center;
  color: #fff;
  font-size: 0.9rem;
  margin-right: 0.3rem;
}
</style>