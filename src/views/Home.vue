<template class="v-application--wrap">
  <v-container class="cards">
    <div>
      <div class="card1" v-show="isShow">
        <form @submit.prevent="onSubmit" @submit="login">
          <v-text-field v-model="email" required label="E-mail"></v-text-field>
          <v-text-field
            v-model="password"
            :counter="10"
            label="password"
            type="password"
            required
          ></v-text-field>

          <v-btn class="bttn" type="submit">submit</v-btn>
        </form>
      </div>
      <div v-show="isShow" class="sideView">
        <v-img
          with="300"
          height="320"
          :src="require('@/assets/image/images9.png')"
          class="img"
        />
        <v-btn id="btnn" @click="change">
          registr
        </v-btn>
      </div>
      <div v-show="!isShow" class="sideView">
        <v-img
          with="300"
          height="320"
          :src="require('@/assets/image/images3.png')"
          class="img"
        />
        <v-btn id="btnn" @click="change">
          login
        </v-btn>
      </div>

      <div class="card2" v-show="!isShow">
        <form @submit.prevent="onSubmit" @submit="registraion">
          <v-text-field
            v-model="name"
            :counter="10"
            label="Name"
            required
          ></v-text-field>

          <v-text-field v-model="email" label="E-mail" required></v-text-field>

          <v-text-field
            v-model="password"
            :counter="10"
            type="password"
            label="password"
            required
          ></v-text-field>

          <v-text-field
            v-model="retyPassword"
            :counter="10"
            label="Rety password"
            type="password"
            required
          ></v-text-field>

          <v-btn class="bttn" type="submit">submit</v-btn>
        </form>
      </div>
    </div>
    <div class="card3">
      <Visit :users="counter"
      :loginN="loginData" />
    </div>
  </v-container>
</template>

<script>
import Visit from "../components/Visit.vue";

export default {
  name: "Home",
  components: {
    Visit,
  },
  data: () => ({
    email: "",
    name: "",
    password: "",
    retyPassword: "",
    isShow: true,
    loginData: [],
    registrationData: [],
    counter: 0,
  }),
  methods: {
    onSubmit() {
      alert("Form has been submitted!");
    },
    login() {
      this.loginData.push(this.email, this.password);
      console.log("login", this.loginData);
      this.counter += 1;
    },
    registraion() {
      this.registrationData.push(
        this.email,
        this.password,
        this.name,
        this.retyPassword
      );

      console.log("register", this.registrationData);
      this.counter += 1;
    },

    change() {
      this.isShow = !this.isShow;
      this.email = null;
      this.password = null;
      this.name = null;
      this.retyPassword = null;
    },
  },
};
</script>

<style>
.v-application--wrap {
  background: #00bf8f;
  background: -webkit-linear-gradient(to right, #001510, #00bf8f);
  background: linear-gradient(to right, #001510, #00bf8f);
  font-family: Georgia, "Times New Roman", Times, serif;
}
.cards {
  width: 100%;
  display: inline-flex;
  justify-content: center;
  margin: 60px;
  margin-right: 40px;
}

.card1 {
  float: left;
  height: 400px;
  padding: 40px;
  margin: 3px;
  background-color: #edf5e0;
  border-radius: 20px 5px;
}
.card2 {
  height: 400px;
  float: left;
  padding: 40px;
  margin: 3px;
  background-color: #f1b92b;
  border-radius: 20px 5px;
}
.card3 {
  height: 120px;
  float: left;
  padding: 40px;
  margin: 3px;
  background-color: #f1b92b;
  border-radius: 20px 5px;
}
#btnn {
  border-radius: 100px;
  width: 100px;
  background-color: #f8cc06;
  color: aliceblue;
  padding: 10px;
  margin-top: 25px;
  margin-left: 15px;

  font-family: Georgia, "Times New Roman", Times, serif;
}

#btnn:hover {
  background-color: #100631;
}

.bttn {
  border-radius: 10px;
}
.sideView {
  height: 400px;
  float: left;
  margin-top: 2px;
  background-color: #d9f1d7;
  /* background: url("@/assets/image/download.png"); */
  border-radius: 20px 0px 0px 20px;
}

.img {
  width: 280px;
  height: 300px;
}

button.bttn.v-btn.v-btn.v-btn--contained.theme--light.v-size--default {
  background-color: #007474;
  border-radius: 20px 20px;
}
</style>
