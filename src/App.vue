<template>
  <div id="app">
    <UserProfile />
  </div>
</template>

<script>
import UserProfile from "@/components/UserProfile";
export default {
  name: "App",
  components: {
    UserProfile,
  },
};
</script>

<style>
body {
  background: #eee;
  margin: 0;
  padding: 2rem;
}

h1,
h2,
h3,
h4,
h5,
h6 {
  margin: 0;
}
</style>
