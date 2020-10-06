<template>
  <div class="app">
    <div class="user">
      <div class="user__panel">
        <h3 class="user__panel-name">@{{ user.username }}</h3>
        <div class="user__panel-badge" v-if="user.isAdmin">Admin</div>
        <p class="user__panel-followers">
          Followers
          <span>{{ followers }}</span>
        </p>
      </div>
      <AddTweet @new-tweet="newTweet" />
    </div>

    <div class="tweets__panel">
      <Tweet
        v-for="tweet in user.tweets"
        :key="tweet.id"
        :username="user.username"
        :tweet="tweet"
        @fav-tweet="favTweet"
      />
    </div>
  </div>
</template>

<script>
import Tweet from "@/components/Tweet";
import AddTweet from "@/components/AddTweet";
import tweetsData from "@/data/tweets";
export default {
  components: {
    Tweet,
    AddTweet,
  },
  data() {
    return {
      followers: 0,
      user: {
        firstname: "Cybertech",
        lastname: "Holma",
        email: "cybertech@gmail.com",
        username: "yasholma",
        isAdmin: true,
        tweets: tweetsData,
      },
    };
  },
  methods: {
    favTweet(id) {
      let tweet = this.user.tweets.find((t) => t.id === id);
      tweet.likes++;
    },
    newTweet(res) {
      const toAddTweet = {
        id: this.user.tweets.length + 1,
        content: res,
        likes: 0,
      };
      this.user.tweets.unshift(toAddTweet);
    },
  },
};
</script>

<style>
.app {
  display: grid;
  grid-template-columns: minmax(20%, 300px) 1fr;
  grid-template-rows: minmax(auto, 12rem);
  gap: 1rem;
}
.user__panel {
  width: 300px;
  background: #fff;
  padding: 1rem;
  box-sizing: border-box;
  box-shadow: 0.3rem 0.2rem 0.2rem rgba(0, 0, 0, 0.3);
  border-radius: 0.3rem;
  cursor: pointer;
  transition: all 0.4s ease-in-out;
}

.user__panel:hover {
  transform: scale(1.01);
}

.user__panel-name {
  font-family: cursive, sans-serif;
  font-size: 2.2rem;
  letter-spacing: 0.1rem;
  margin-bottom: 1rem;
}

.user__panel-badge {
  background: rebeccapurple;
  color: #fff;
  border-radius: 0.3rem;
  font-weight: bold;
  display: inline-block;
  padding: 0.3rem;
}

.user__panel-followers {
  display: flex;
  flex-direction: column;
  color: #aaa;
  margin-top: 1.5rem;
}

.user__panel-followers span {
  color: #212226;
  margin-top: 0.3rem;
}
</style>