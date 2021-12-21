<script setup lang="ts">
import { ref } from "vue";

let input = ref("");
let dark = ref(false);

let a=false

let todos = ref([
  {
    todo: "todo11",
    done: ref(false),
  },
]);

function add() {
  if (input.value === "") return;
  todos.value.push({
    todo: input.value,
    done: false,
  });
  input.value = "";
}

function remove(index: number) {
  todos.value.splice(index, 1);
  console.log(todos);
}

function Dark() {
  dark.value = !dark.value;
}

</script>

<template>
  <div
    class="
      w-screen
      h-screen
      bg-gradient-to-br
      from-green-600
      to-blue-400
      filter
      blur
    "
  ></div>
  <div class="w-screen h-screen absolute top-0">
    <div
      :class="{ ' dark:bg-black': dark }"
      class="
        max-w-xl
        md:max-w-3xl
        bg-white
        py-20
        flex flex-col
        gap-6
        items-center
        px-5
        mx-auto
        mt-16
        rounded-lg
        relative
        overflow-hidden
        shadow-xl
      "
    >
      <button @click="Dark">
        <svg
          xmlns="http://www.w3.org/2000/svg"
          v-if="dark === false"
          class="h-5 w-5"
          viewBox="0 0 20 20"
          fill="currentColor"
        >
          <path
            d="M17.293 13.293A8 8 0 016.707 2.707a8.001 8.001 0 1010.586 10.586z"
          />
        </svg>
        <svg
          xmlns="http://www.w3.org/2000/svg"
          v-else
          class="h-7 w-7 text-white"
          viewBox="0 0 20 20"
          fill="currentColor"
        >
          <path
            fill-rule="evenodd"
            d="M10 2a1 1 0 011 1v1a1 1 0 11-2 0V3a1 1 0 011-1zm4 8a4 4 0 11-8 0 4 4 0 018 0zm-.464 4.95l.707.707a1 1 0 001.414-1.414l-.707-.707a1 1 0 00-1.414 1.414zm2.12-10.607a1 1 0 010 1.414l-.706.707a1 1 0 11-1.414-1.414l.707-.707a1 1 0 011.414 0zM17 11a1 1 0 100-2h-1a1 1 0 100 2h1zm-7 4a1 1 0 011 1v1a1 1 0 11-2 0v-1a1 1 0 011-1zM5.05 6.464A1 1 0 106.465 5.05l-.708-.707a1 1 0 00-1.414 1.414l.707.707zm1.414 8.486l-.707.707a1 1 0 01-1.414-1.414l.707-.707a1 1 0 011.414 1.414zM4 11a1 1 0 100-2H3a1 1 0 000 2h1z"
            clip-rule="evenodd"
          />
        </svg>
      </button>
      <div
        :class="{ 'dark:bg-sky-900 dark:shadow-none': dark }"
        class="
          w-5
          rounded-full
          shadow-lg shadow-gray-600/30
          absolute
          -top-10
          bg-sky-500
          h-20
        "
      ></div>
      <div
        :class="{ 'dark:bg-sky-900 dark:shadow-none': dark }"
        class="
          w-5
          rounded-full
          shadow-lg shadow-gray-600/30
          absolute
          ml-14
          -top-14
          bg-sky-600
          h-20
        "
      ></div>
      <div
        :class="{ 'dark:bg-sky-900 dark:shadow-none': dark }"
        class="
          w-5
          rounded-full
          shadow-lg shadow-gray-600/30
          absolute
          mr-14
          -top-14
          bg-sky-600
          h-20
        "
      ></div>
      <h1
        :class="{ 'dark:text-gray-100': dark }"
        class="text-center font-bold text-5xl font-mono text-sky-600"
      >
        Todo-App
      </h1>
      <div
        :class="{ 'dark:bg-zinc-900': dark }"
        class="
          bg-gray-300
          w-[500px]
          md:w-[550px]
          rounded-lg
          px-3
          py-3
          space-y-2
          mt-5
        "
      >
        <div v-for="(tode, index) in todos" class="flex justify-between">
          <p
            :class="
              { 'line-through text-gray-600': tode.done },{ ' dark:text-gray-100': dark } 
            "
            class="text-xl font-semibold tracking-wide"
          >
            {{ tode.todo }}
          </p>
          <div class="flex space-x-2">
            <button v-if="tode.done === true" @click="remove(index)">
              <svg
                xmlns="http://www.w3.org/2000/svg"
                class="h-8 w-6 text-red-500 animate-pulse"
                viewBox="0 0 20 20"
                fill="currentColor"
              >
                <path
                  fill-rule="evenodd"
                  d="M9 2a1 1 0 00-.894.553L7.382 4H4a1 1 0 000 2v10a2 2 0 002 2h8a2 2 0 002-2V6a1 1 0 100-2h-3.382l-.724-1.447A1 1 0 0011 2H9zM7 8a1 1 0 012 0v6a1 1 0 11-2 0V8zm5-1a1 1 0 00-1 1v6a1 1 0 102 0V8a1 1 0 00-1-1z"
                  clip-rule="evenodd"
                />
              </svg>
            </button>
            <button @click="tode.done = true" v-if="tode.done === false">
              <svg
                xmlns="http://www.w3.org/2000/svg"
                class="h-8 w-8 text-green-600"
                viewBox="0 0 20 20"
                fill="currentColor"
              >
                <path
                  fill-rule="evenodd"
                  d="M6.267 3.455a3.066 3.066 0 001.745-.723 3.066 3.066 0 013.976 0 3.066 3.066 0 001.745.723 3.066 3.066 0 012.812 2.812c.051.643.304 1.254.723 1.745a3.066 3.066 0 010 3.976 3.066 3.066 0 00-.723 1.745 3.066 3.066 0 01-2.812 2.812 3.066 3.066 0 00-1.745.723 3.066 3.066 0 01-3.976 0 3.066 3.066 0 00-1.745-.723 3.066 3.066 0 01-2.812-2.812 3.066 3.066 0 00-.723-1.745 3.066 3.066 0 010-3.976 3.066 3.066 0 00.723-1.745 3.066 3.066 0 012.812-2.812zm7.44 5.252a1 1 0 00-1.414-1.414L9 10.586 7.707 9.293a1 1 0 00-1.414 1.414l2 2a1 1 0 001.414 0l4-4z"
                  clip-rule="evenodd"
                />
              </svg>
            </button>
            <button v-if="tode.done === true" @click="tode.done = false">
              <svg
                xmlns="http://www.w3.org/2000/svg"
                class="h-8 w-6 text-green-500"
                viewBox="0 0 20 20"
                fill="currentColor"
              >
                <path
                  fill-rule="evenodd"
                  d="M4 2a1 1 0 011 1v2.101a7.002 7.002 0 0111.601 2.566 1 1 0 11-1.885.666A5.002 5.002 0 005.999 7H9a1 1 0 010 2H4a1 1 0 01-1-1V3a1 1 0 011-1zm.008 9.057a1 1 0 011.276.61A5.002 5.002 0 0014.001 13H11a1 1 0 110-2h5a1 1 0 011 1v5a1 1 0 11-2 0v-2.101a7.002 7.002 0 01-11.601-2.566 1 1 0 01.61-1.276z"
                  clip-rule="evenodd"
                />
              </svg>
            </button>
          </div>
        </div>
        <p
          v-if="todos.length === 0"
          :class="{ 'dark:text-white': dark }"
          class="text-center text-xl text-gray-600 animate-pulse"
        >
          Empty
        </p>
      </div>
      <div class="w-[500px] md:w-[550px] flex space-x-2">
        <input
          v-model="input"
          :class="{
            'dark:shadow-md dark:bg-black dark:text-white dark:shadow-blue-600/50':
              dark,
          }"
          class="
            py-1
            px-4
            flex-1
            outline-none
            shadow-md
            rounded-lg
            border border-sky-500
          "
          placeholder="Enter your todo"
          type="text"
        />
        <button @click="add">
          <svg
            xmlns="http://www.w3.org/2000/svg"
            class="h-9 w-9 text-sky-600 hover:text-sky-500"
            viewBox="0 0 20 20"
            fill="currentColor"
          >
            <path
              fill-rule="evenodd"
              d="M10 18a8 8 0 100-16 8 8 0 000 16zm1-11a1 1 0 10-2 0v2H7a1 1 0 100 2h2v2a1 1 0 102 0v-2h2a1 1 0 100-2h-2V7z"
              clip-rule="evenodd"
            />
          </svg>
        </button>
      </div>
      <h1 class="text-gray-800 tracking-wide" :class="{ 'dark:text-white': dark }">
        Todos : {{ todos.length }}
      </h1>
    </div>
  </div>
</template>
