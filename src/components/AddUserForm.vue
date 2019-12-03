<template>
  <form>

    <h2>Add new user: </h2>

    <label for="name">Name: </label>
    <input id="name" v-model="name" type="text" />
    <br>

    <label for="email">Email: </label>
    <input id="email" v-model="email" type="email" />
    <br>

    <label for="phone">Phone: </label>
    <input id="phone" v-model="phone" type="phone" />

    <User :user="newUser" />

    <button @click.prevent="addUser">Add user</button>

  </form>
</template>

<script>
import User from './User';

export default {
  name: 'AddUserForm',
  components: {
    User
  },
  props: ['lastUserId'],
  data () {
    return {
      name: '',
      email: '',
      phone: ''
    }
  },
  computed: {
    newUser () {
      return {
        id: this.lastUserId + 1,
        name: this.name,
        email: this.email,
        phone: this.phone
      }
    }
  },
  methods: {
    addUser () {
      this.$emit('addUser', this.newUser);
    }
  }
};
</script>

<style scoped>
form {
  width: 330px;
  margin-right: 30px;
}
label {
  display: inline-block;
  min-width: 70px;
}
input {
  margin-top: 12px;
}
input:first-of-type {
  margin-top: 20px;
}
input:last-of-type {
  margin-bottom: 17px;
}
button {
  margin-top: 20px;
  font-size: 1.2rem;
}
</style>
