<script setup lang="ts">
import { RouterLink, RouterView } from 'vue-router';
// import SignUp from './components/SignUp.vue';
import Toastr from './components/Toastr.vue';
// interface hello {
//   message: string;
//   type: string;
// }
// interface Props {
//   message: string;
//   type: string;
// }
// const { message, type } = defineProps<Props>();
const variables = [
  {
    message: 'Hello',
    type: 'success',
  },
  {
    message: 'Hello',
    type: 'error',
  },
  {
    message: 'Hello',
    type: 'success',
  },
  {
    message: 'Hello',
    type: 'error',
  },
  {
    message: 'Hello',
    type: 'success',
  },
];
</script>

<template>
  <div class="toast-container">
    <div v-for="(variable, index) in variables" :key="index" class="asd">
      <Toastr :message="variable.message" :type="variable.type" />
    </div>
  </div>

  <!-- <SignUp /> -->
  <header>
    <img
      alt="Vue logo"
      class="logo"
      src="@/assets/1_grnHpaP0BQMrHbcaJfZwIQ.png"
      width="125"
      height="125"
    />

    <div class="wrapper">
      <nav>
        <RouterLink to="/">Home</RouterLink>
        <RouterLink to="/signup">Signup</RouterLink>
        <RouterLink to="/about">About</RouterLink>
        <RouterLink to="/order">Order Now</RouterLink>
        <RouterLink to="/login">Login</RouterLink>
      </nav>
    </div>
  </header>

  <RouterView />
</template>

<style scoped>
header {
  line-height: 1.5;
  max-height: 100vh;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

nav {
  width: 100%;
  font-size: 12px;
  text-align: center;
  margin-top: 2rem;
}
.toast-container {
  position: fixed;
  display: flex;
  flex-direction: column;
  float: left;
  margin-top: 50px;
  top: 4px;
  right: 30px;
  border-radius: 12px;
  padding: 20px 35px 20px 25px;
  box-shadow: 0 6px 20px -5px rgba(0, 0, 0, 0.1);
  overflow: hidden;
  transform: translateX(calc(100% + 30px));
  transition: all 0.5s cubic-bezier(0.68, -0.55, 0.265, 1.35);
  width: 300px;
  z-index: 9999999;
}
nav a {
  display: inline-block;
  padding: 0 1rem;
  border-left: 1px solid var(--color-border);
}

nav a:first-of-type {
  border: 0;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }

  nav {
    text-align: left;
    margin-left: -1rem;
    font-size: 1rem;

    padding: 1rem 0;
    margin-top: 1rem;
  }
  .asd {
    z-index: 1;
    /* position: fixed; */
  }
}
</style>
