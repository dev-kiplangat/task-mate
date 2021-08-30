<template>
  <div class="row login-box">
    <div class="col-8 shadow-platform"></div>

    <div class="col-4 column items-center justify-center log-box">
      <div class="logo"></div>
      <div class="text-h5 q-mb-lg">Task-Mate</div>

      <q-form @submit="onSubmit" style="min-width: 300px" class="q-gutter-md">
        <q-input
          outlined
          dense
          type="email"
          v-model="email"
          class="fork"
          label="Your email *"
          hint="Email address"
          lazy-rules
          :rules="[(val) => (val && val.length > 0) || 'Please type something']"
        />

        <q-input
          v-model="password"
          class="fork"
          outlined
          dense
          :type="isPwd ? 'password' : 'text'"
          label="Your password *"
          lazy-rules
          :rules="[(val) => (val && val.length > 5) || 'password too short']"
        >
          <template v-slot:append>
            <q-icon
              :name="isPwd ? 'visibility_off' : 'visibility'"
              class="cursor-pointer"
              @click="isPwd = !isPwd"
            />
          </template>
        </q-input>

        <div>
          <q-btn
            dense
            type="submit"
            :loading="loading"
            label="Login"
            style="color: #fff"
            icon="login"
            class="q-my-sm full-width"
          >
            <template v-slot:loading>
              <q-spinner-facebook />
            </template>
          </q-btn>
        </div>

        <div class="q-my-lg text-center alpha">
          <span>New Here?</span>
          <router-link class="router__link" to="/register">
            Create An Account
          </router-link>
        </div>
      </q-form>
    </div>
  </div>
</template>

<script>
import http from "@/utils/http-common";

export default {
  name: "login",
  data() {
    return {
      email: "",
      password: "",
      loading: false,
      isPwd: true,
    };
  },
  created() {
    window.localStorage.removeItem("not_new");
    const error = window.localStorage.getItem("logout");

    if (error == null) {
      return;
    }
    this.showNotif(error, "bottom");
    window.localStorage.removeItem("logout");
  },
  methods: {
    async onSubmit() {
      try {
        this.loading = true;
        const res = await http.post("/login", {
          email: this.email,
          password: this.password,
        });

        if (res.data.success == false) {
          this.showNotif(res.data.message);
          this.loading = false;

          return;
        }

        window.localStorage.setItem("token", res.data.token);
        // set the token

        this.$router.push({ path: "/app" });
        this.loading = false;
      } catch (err) {
        console.log(err);
      }
    },
    showNotif(message, position = "top") {
      this.$q.notify({
        message: message,
        icon: "report_problemt",
        color: "negative",
        multiline: true,

        timeout: 1000,
        position: position,
      });
    },
  },
};
</script>

<style lang="scss" scoped>
.logo {
  height: 80px;
  position: relative;
}

.logo::after,
.logo::before {
  content: "";
  position: absolute;
}
.alpha {
  font-size: 15px;
  font-weight: 600;
}
.logo::before {
  background: aqua;
  top: 10px;
  left: 0px;
  height: 48px;
  width: 12px;
  border-radius: 15px;
  transform: rotate(40deg);
}

.logo::after {
  background: orange;
  top: 15px;
  left: 22px;
  height: 35px;
  width: 12px;
  border-radius: 15px;
  transform: rotate(40deg);
}

.full-width {
  width: 100%;
  padding: 0.4em 0 !important;
  background: #11ca92fb;
  color: #fff !important;
  font-size: 14px;
  font-weight: 600;
}
.login-box {
  min-height: 100vh;
}

.shadow-platform {
  background: linear-gradient(-45deg, orange, transparent),
    url("../assets/leader.jpg");
  background-size: cover;
}

.logo {
  padding: 1rem 0;
  text-align: center;
}

.router__link {
  text-decoration: none;
  color: #1186cafb;
  border-bottom: 1px dotted #1186cafb;
}
</style>
