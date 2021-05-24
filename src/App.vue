<template>
  <div id="app">
    <!-- header section -->
    <div class="header text-center mt-5 mb-5">
      <h1>Users Card</h1>
    </div>

    <div class="card-wrap d-flex justify-content-center">
      <!-- card section -->
      <div class="container row row-cols-md-3">
        <!-- looping data from axios -->
        <div v-for="user in users" :key="user">
          <!-- card data start -->
          <b-card
            :img-src="user.picture.large"
            img-alt="Image"
            img-top
            tag="article"
            style="max-width: 20rem"
            class="card mr-3 mb-5"
          >
            <b-card-text>
              <p>
                Name:
                <strong>{{ user.name.first }} {{ user.name.last }}</strong>
              </p>
              <a :href="user.email">Email address: {{ user.email }}</a>
              <p>
                Telephone: {{ user.phone }}
                <br />
                Mobile: {{ user.cell }}
                <br />
                Country: {{ user.location.country }}
              </p>
            </b-card-text>
          </b-card>
          <!-- card data end -->
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "App",
  data() {
    return {
      users: "",
    };
  },

  created() {
    axios
      .get("https://randomuser.me/api/?results=20")
      .then((response) => (this.users = response.data.results));
  },
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
</style>