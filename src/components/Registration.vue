<template>
  <div class="to_Center_Div">
    <div class="central_box">
      <div class="box_with_padding">
        <div class="left_box">
          <v-form ref="form" v-model="valid" lazy-validation>
            <v-col>
              <div class="Fundoo_logo">
                <!-- <span>Fundoo Notes</span> -->
                <span class="f">F</span>
                <span class="u">u</span>
                <span class="n">n</span>
                <span class="d">d</span>
                <span class="o">o</span>
                <span class="oo">o</span>
              </div>
              <div class="create_tag">
                <div>
                  <span>Create your Fundoo Account</span>
                </div>
              </div>
              <div class="first_last_name">
                <v-text-field
                  v-model="FirstName"
                  :rules="nameRules"
                  label="FirstName"
                  required
                  outlined
                >
                </v-text-field>

                <v-text-field
                  v-model="LastName"
                  :rules="nameRules"
                  label="LastName"
                  required
                  outlined
                ></v-text-field>
              </div>
              <div class="email">
                <v-text-field
                  v-model="email"
                  :rules="emailRules"
                  label="E-mail"
                  required
                  outlined
                >
                </v-text-field>
              </div>
              <div class="password">
                <v-text-field
                  v-model="Password"
                  type="password"
                  label="Password"
                  required
                  outlined
                >
                </v-text-field>

                <v-text-field
                  v-model="Confirm"
                  type="password"
                  label="Confirm"
                  required
                  outlined
                >
                </v-text-field>
              </div>

              <v-checkbox
                v-model="checkbox"
                :rules="[(v) => !!v || 'You must agree to continue!']"
                label="Do you agree?"
                required
              ></v-checkbox>
              <div>
                <a
                  href="http://localhost:8080/login"
                  style="text-decoration: none"
                  >Sign in instead</a
                >
              </div>
              <div class="button">
                <v-btn
                  :disabled="!valid"
                  color="#4285F4"
                  class="mr-4"
                  @click="validate"
                >
                  Next
                </v-btn>
              </div>
            </v-col>
          </v-form>
        </div>
        <div class="right_box">
          <img
            src="../assets/account.svg"
            alt="Image"
            width="244"
            height="244"
          />
        </div>
      </div>
    </div>
  </div>
</template>
<script>
import UserService from "@/services/userService/userService";
export default {
  name: "RegistrationComponent",
  data: () => ({
    valid: true,
    FirstName: "",
    LastName: "",
    email: "",
    Password: "",
    Confirm: "",
    Next: "",
    checkbox: "",
    nameRules: [
      (v) => !!v || "Name is required",
      (v) => (v && v.length <= 10) || "Name must be less than 10 characters",
    ],

    emailRules: [
      (v) => !!v || "E-mail is required",
      (v) => /.+@.+\..+/.test(v) || "E-mail must be valid",
    ],
  }),

  methods: {
    validate() {
      this.$refs.form.validate();
      console.log(this.FirstName);
      console.log(this.LastName);
      console.log(this.email);
      console.log(this.Password);
      console.log(this.Confirm);
      let reqData = {
        firstname: this.FirstName,
        lastname: this.LastName,
        email: this.email,
        password: this.Password,
        password_confirmation: this.Confirm,
      };
      UserService.prototype
        .registrationService(reqData)
        .then((data) => {
          console.log("Response from Registration", data);
        })
        .catch((error) => {
          console.log(error);
        });
    },
  },
};
</script>
<style>
.to_Center_Div {
  display: flex;
  justify-content: center;
  align-content: center;
  margin: 70px;
}

.central_box {
  width: 700px;
  height: 500px;
  padding: 48px 40px 36px 40px;
  margin: 0;
  border-style: solid;
  border-width: 1px;
  border-color: #9a9a9c;
  border-radius: 5px;
  box-sizing: content-box;
}

.box_with_padding {
  display: flex;
}

.left_box {
  width: 354px;
  height: 400px;
}

.first_last_name {
  height: -30px;
  width: 75%;
  display: flex;
  flex-direction: row;
  gap: 40px;
}
.create_tag {
  font-family: "sans-serif";
  font-size: 24px;
}
.email {
  width: 270px;
}
.password {
  width: 80%;
  display: flex;
  flex-direction: row;
  gap: 30px;
}
.next {
  left: 10px;
  right: 10px;
  padding-left: 220px;
  margin-top: -30px;
}
.f {
  color: blue;
  font-weight: bold;
  font-family: sans-serif;
  text-align: center;
}

.u {
  color: red;
  font-weight: bold;
  font-family: sans-serif;
  text-align: center;
}

.n {
  color: yellow;
  font-weight: bold;
  font-family: sans-serif;
  text-align: center;
}

.d {
  color: blue;
  font-weight: bold;
  font-family: sans-serif;
  text-align: center;
}

.o {
  color: green;
  font-weight: bold;
  font-family: sans-serif;
  text-align: center;
}

.oo {
  color: red;
  font-weight: bol;
}
.right_box {
  width: 100px;
  height: 300px;
  padding-left: 90px;
  display: flex;
  justify-content: center;
  align-items: center;
}

.button {
  display: flex;
  flex-flow: row wrap;
  justify-content: space-between;
  align-items: center;
  padding-bottom: 20px;
  margin-top: -30px;
  margin-left: 200px;
}
</style>