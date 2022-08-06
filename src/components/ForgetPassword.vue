<template>
  <div class="centrealign">
    <div class="centerebox">
      <div class="box_with_paddingg">
        <div class="leftBox">
          <v-form ref="form" v-model="valid" lazy-validation>
            <v-col>
              <div class="fundoo_logo">
                <!-- <span>Fundoo Notes</span> -->
                <span class="f">F</span>
                <span class="u">u</span>
                <span class="n">n</span>
                <span class="d">d</span>
                <span class="o">o</span>
                <span class="oo">o</span>
              </div>
              <div class="heading_tag">
                
                  <h3>ForgetPassword</h3>
                
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
              
              <!-- <div class="paragraph">
                <p>Not your computer? Use Guest mode to sign in privately.</p>
             
              <div>
                <a
                  href="http://localhost:8080/forget"
                  class="Forget_password"
                  width="368"
                  height="20"
                  >Forget password</a
                >
              </div>
              </div> -->
             <div class="reset_button">
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
      </div>
    </div>
  </div>
</template>

<script>
import UserService from '@/services/userService/userService';

export default {
  name: "ForgetPasswordComponent",
  data: () => ({
    valid: true,

    Password: "",

    passwordRules: [
      (v) => !!v || "password is required",
      (v) => (v && v.length <= 10) || "password must be less than 10 characters",
    ],
    email: "",
    emailRules: [
      (v) => !!v || "E-mail is required",
      (v) => /.+@.+\..+/.test(v) || "E-mail must be valid",
    ],
  }),

  methods: {
    validate() {
      this.$refs.form.validate();
      console.log(this.email);
      let reqData= {
        email:this.email,
        
      }
    UserService.prototype.forgetPasswordService(reqData).then((data)=>{
        console.log("Response from forgotPassword",data);
    }).catch((error)=>{
        console.log(error);
    })

    },
      
  },

};
</script>
<style>
.centrealign {
  display: flex;
  justify-content: center;
  align-content: center;
  margin: 70px;
}

.centerebox {
  width: 310px;
  height: 300px;
  padding: 48px 40px 36px 40px;
  margin: 0;
  border-style: solid;
  border-width: 1px;
  border-color: #9a9a9c;
  border-radius: 5px;
  box-sizing: content-box;
}

.box_with_paddingg {
  display: flex;
}

.leftBox {
  width: 300px;
  height: 400px;
}

.first_last_name {
  width: 75%;
  display: flex;
  flex-direction: row;
  gap: 40px;
}

.create_tag {
  font-family: "sans-serif";
  font-size: 24px;
  align-content: center;
}

.email {
  width: 270px;
}

.password {
  width: 270px;
  display: flex;
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

.reset_button {
  display: flex;
  flex-flow: row wrap;
  justify-content: space-between;
  align-items: center;
  padding-bottom: 20px;
  margin-top: 30px;
  margin-left: 80px;
}
.fundoo_logo {
  padding-bottom: -30px;
  padding-left: 100px;
  padding-top: 10px;
  /* height: 100px; */
  /* height: 10px; */
  width: 10px;
}
.heading_tag {
  width: 368px;
  height: 50px;
  padding-top: 20px;
  padding-left: 60px;
  box-sizing: border-box;
}
.paragraph {
  padding-left: 10px;
}
</style>