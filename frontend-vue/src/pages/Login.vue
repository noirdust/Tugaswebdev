<template>
  <div class="container">
    <div class="col-md-6 m-auto"></div>
    <h1>Login Page</h1>
    <div>
      <div class="mb-3">
        <label for="exampleFormControlInput1" class="form-label"
          >Email address</label
        >
        <input
          type="email"
          class="form-control"
          id="exampleFormControlInput1"
          placeholder="name@example.com"
          v-model="form.email"
        />
      </div>
      <div class="mb-3">
        <label for="exampleFormControlInput1" class="form-label"
          >Password</label
        >
        <input
          type="password"
          class="form-control"
          id="exampleFormControlInput1"
        />
      </div>
      <div>
        <button type="submit" class="btn btn-primary">Login</button>
      </div>
    </div>
  </div>
</template>
<script setup>
import { ref } from "vue";
import axios from "axios";

import { useRouter } from "vue-router";

const router = useRouter();

const form = ref({
  email: "",
  password: "",
});

const submitLogin = async () => {
  await axios.post("/Login", {
    email: form.value.email,
    password: form.value.password,
  });

  router.push("/");
};
</script>
