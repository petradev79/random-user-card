<template>
  <div class="container">
    <div class="left">
      <Text />
      <Button :user="user" @getUser="getUser" :class="user.gender" />
    </div>
    <div class="right">
      <Card :user="user" v-if="user && Object.keys(user).length" />
      <div>
        <h1>{{ errorMessage }}</h1>
      </div>
    </div>
  </div>
</template>

<script>
import { API_URL } from './config.js';
import Button from './components/Button';
import Card from './components/Card';
import Text from './components/Text';

export default {
  name: 'App',
  components: { Button, Card, Text },
  data() {
    return {
      user: {},
      errorMessage: ''
    };
  },
  mounted() {
    this.getUser();
  },
  methods: {
    async getUser() {
      try {
        const res = await fetch(API_URL);
        if (!res.ok)
          throw new Error(
            `Something went wrong! Please try again :) (${res.status})`
          );

        const { results } = await res.json();
        const data = results[0];

        this.user.firstName = data.name.first;
        this.user.lastName = data.name.last;
        this.user.email = data.email;
        this.user.gender = data.gender;
        this.user.picture = data.picture.large;
        this.user.title = data.name.title;
        this.user.phone = data.phone;
        this.user.streetNumber = data.location.street.number;
        this.user.streetName = data.location.street.name;
        this.user.city = data.location.city;
        this.user.country = data.location.country;
      } catch (err) {
        this.errorMessage = err.message;
      }
    }
  }
};
</script>

<style lang="scss">
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300;900&display=swap');

*,
::after,
::before {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
html {
  font-family: 'Poppins', sans-serif;
  font-size: 62.5%;
  font-weight: 300;
  background: #dacabc;
  color: #181818;
}
.container {
  height: 100vh;
  width: 100%;
  max-width: 100rem;
  margin: 0 auto;
  padding: 1rem;
  display: flex;
  justify-content: space-between;
  align-items: center;
}
</style>
