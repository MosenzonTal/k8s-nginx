<template>
  <div>
    <q-table :rows="users" :columns="columns" row-key="id"> </q-table>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  name: 'UserView',
  data() {
    return {
      users: [],
      columns: [
        {
          name: 'PersonID',
          label: 'Person ID',
          field: 'PersonID',
          align: 'left',
        },
        {
          name: 'FirstName',
          label: 'First Name',
          field: 'FirstName',
          align: 'left',
        },
        {
          name: 'LastName',
          label: 'Last Name',
          field: 'LastName',
          align: 'left',
        },
      ],
    };
  },
  methods: {
    fetchUsers() {
      // Use Axios to make an API call to fetch users
      axios
        .get('http://localhost:3000/persons')
        .then((response) => {
          // Handle the response and update the users data property
          this.users = response.data;
          console.log(this.users);
        })
        .catch((error) => {
          // Handle any errors
          console.error('Failed to fetch users:', error);
        });
    },
  },
  mounted() {
    // Fetch users when the component is mounted
    this.fetchUsers();
  },
};
</script>
