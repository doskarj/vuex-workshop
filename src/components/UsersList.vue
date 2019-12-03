<template>
  <div class="users-list">

    <h2>Users list: ({{ usersCount }} users)</h2>
    <User v-for="user in users" :key="user.id" :user="user" :isRemovable="true" @removeUser="removeUser" />

  </div>
</template>

<script>
import User from './User.vue';

export default {
  name: 'UsersList',
  components: {
    User
  },
  props: ['users'],
  computed: {
    usersCount () {
      return this.users.length;
    }
  },
  methods: {
    removeUser (userId) {
      this.$emit('removeUser', userId);
    }
  }
};
</script>

<style scoped>
.users-list {
  display: flex;
  flex-direction: column;
}
</style>
