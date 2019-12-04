<template>
  <div>

    <h1>vuex-workshop</h1>

    <main>
      <AddUserForm @addUser="addUser" :lastUserId="lastUserId" />
      <UsersList :users="users" @removeUser="removeUser" />
    </main>

  </div>
</template>

<script>
import users from './assets/dummyUsers.js';
import AddUserForm from './components/AddUserForm.vue';
import UsersList from './components/UsersList.vue';

export default {
  name: 'App',
  components: {
    AddUserForm,
    UsersList
  },
  data () {
    return {
      users
    }
  },
  computed: {
    lastUserId () {
      return this.users && this.users.length > 0 ? this.users[this.users.length - 1].id : 0;
    }
  },
  methods: {
    addUser (newUser) {
      this.users.push(newUser);
    },
    removeUser (userId) {
      this.users = this.users.filter(user => user.id !== userId);
    }
  }
}
</script>

<style>
html {
  font-family: Arial, sans-serif;
  color: #2c3e50;
}
main {
  display: flex;
}
h2 {
  margin-bottom: 5px;
}
</style>
