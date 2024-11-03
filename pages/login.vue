<template>
  <form @submit.prevent="user.login">
    <h1>Login</h1>
    <label> username <input type="text" /> </label>
    <label> password <input type="password" /> </label>
    <button>Login</button>
  </form>
</template>

<script setup>
const user = useUser();
definePageMeta({
  layout: "plain",
});
</script>
