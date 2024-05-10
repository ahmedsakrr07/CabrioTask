<template>
  <div class="bg-black text-white py-3.5 px-6 shadow md:flex items-center">
    <div class="flex items-center">
        <img src="../assets/logo2.png" alt="logo" class="logotype"  />
    </div>
   <img src="../assets/menu.png" @click="menue()" class="block h-7 w-7 absolute left-12px md:hidden top-[17px] cursor-pointer" style="color: white;"/> 
    <ul
      class="md:flex md:items-center md:px-0 px-8 md:pb-0 pb-10"
      :class="[open ? 'block' : 'hidden']"
    >
      <li v-for="link in links" :key="link" class="md:mx-4 md:my-0 my-4 md:ml-[50px]">
        <a :href="link.link" class="text-white links">{{ link.name }}</a>
      </li>
    </ul>
    <div class="absolute text-white text-sm inset-y-0 right-[14.5rem] pt-2 md:block hidden">
      <div class="hidden sm:block">Balance</div>
      <div class="font-semibold">50,600.0 SAR</div>
    </div>

    <div class="logo absolute text-white text-sm inset-y-0 right-[10.5rem] pt-3 md:block hidden">
      <img class="h-8 w-8 rounded-full" src="../assets/logo.jpg" />
    </div>
    <div class="absolute text-white text-sm inset-y-0 right-[4.5rem] pt-3 md:block hidden">
      <div class="hidden font-semibold sm:block">Khuzimah A.</div>
      <div class="text-xs">Cabrio Co.</div>
    </div>

    <div class="absolute text-white text-sm inset-y-0 right-[1rem] pt-3 md:block hidden">
      <div>
        <button
          type="button"
          class="w-full gap-x-1.5 rounded-m px-3 py-2 text-sm font-semibold text-white"
          id="menu-button"
          aria-expanded="true"
          aria-haspopup="true"
          @click="menue()"
        >
          <svg
            class="-mr-1 h-5 w-5 text-white"
            viewBox="0 0 20 20"
            fill="currentColor"
            aria-hidden="true"
          >
            <path
              fill-rule="evenodd"
              d="M5.23 7.21a.75.75 0 011.06.02L10 11.168l3.71-3.938a.75.75 0 111.08 1.04l-4.25 4.5a.75.75 0 01-1.08 0l-4.25-4.5a.75.75 0 01.02-1.06z"
              clip-rule="evenodd"
            />
          </svg>
        </button>
      </div>
      <div
        class="absolute right-0 z-10 mt-6 w-56 origin-top-right rounded-md bg-white shadow-lg ring-1 ring-black ring-opacity-5 focus:outline-none"
        role="menu"
        aria-orientation="vertical"
        aria-labelledby="menu-button"
        tabindex="-1"
        :class="[open ? 'block' : 'hidden']"
      >
        <div class="py-1" role="none">
          <div class="flex items-center ">
            <img src="../assets/setting.png" style="width: 15px;height: 15px; margin-left: 11px;" />
            <a
            href="#"
            class="text-black block font-[500] px-4 py-2 text-sm"
            role="menuitem"
            tabindex="-1"
            id="menu-item-0"
            >Profile Settings</a
          >
          </div>
          <hr />
          <div class="flex gap-1 items-center ">
            <img src="../assets/translate.png" style="width: 15px;height: 15px; margin-left: 11px;" />
          <a
            href="#"
            class="text-black block font-[500] px-4 py-2 text-sm"
            role="menuitem"
            tabindex="-1"
            id="menu-item-1"
            >العربيه</a
          >
          </div>
          <button
                  type="submit"
                  class="border-2 rounded-lg pb-[5px] pt-[5px] pl-2 mt-4 text-sm font-semibold border-black text-black"
                  style="width: 91%;margin-left: 13px;margin-top: 8px;margin-bottom: 10px;"
                >
                  Logout
                </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { ref } from "vue";

export default {
  setup() {
    let open = ref(false);

    let links = [
      { name: "Compony profile", link: "#" },
      { name: "Book a Ride", link: "#" },
      { name: "Rides", link: "#" },
    ];

    function menue() {
      open.value = !open.value;
    }

    return { links, open, menue };
  },
};
</script>

<style>
.logotype  {
  width: 138.65px;
    height: 28px;
    margin-left: 39px;

}
.links {
  font-size: 14px;
  font-weight: 400;
  line-height: 17.64px;
  text-align: right;
}
</style>
