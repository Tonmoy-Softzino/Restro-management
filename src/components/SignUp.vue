<template>
  <div
    class="flex justify-center items-center bg-white px-20 font-medium py-16 rounded flex-col"
  >
    <h1 class="font-5xl text-slate-500 font-bold text-5xl mb-2">SignUp</h1>
    <img
      src="https://img.freepik.com/premium-vector/restaurant-logo-design-template_79169-56.jpg?w=2000"
      alt="Loading..."
      class="w-[220px] h-[220px]"
    />
    <form action="#" class="flex flex-col">
      <label for="name">
        <div class="text-black">Name</div>
        <input
          type="text"
          placeholder="Name"
          name="name"
          class="px-2 py-1 w-[18rem] h-[2.5rem] mt-1 border border-black rounded box-border text-black"
        />
      </label>
      <label for="email" class="mt-2">
        <div class="text-black">Email</div>
        <input
          type="text"
          placeholder="Email"
          name="email"
          class="px-2 py-1 w-[18rem] h-[2.5rem] mt-1 border border-black rounded box-border text-black"
        />
      </label>
      <label for="password" class="mt-2">
        <div class="text-black">Password</div>
        <input
          type="password"
          name="password"
          placeholder="Password"
          class="px-2 py-1 w-[18rem] h-[2.5rem] mt-1 text-black border border-black rounded"
        />
      </label>
      <button class="bg-slate-500 mt-4 text-black px-12 py-2 rounded">
        Signup
      </button>
    </form>
  </div>
</template>
