<script setup lang="ts">
    const route = useRoute();
    
    const activeLink = (path: string): string => {
      return route.path === path 
        ? 'bg-white text-gray-700 hover:bg-blue-600 ' 
        : 'text-white';
    }

    const isSubmenuHidden = ref(true);

    const toggleDropdown = () => {
        isSubmenuHidden.value = !isSubmenuHidden.value;
    };

    toggleDropdown();

</script>
<template>
    <div class="bg-blue-600">
      <div
        class="sidebar fixed top-0 bottom-0 lg:left-0 p-2 w-[300px] overflow-y-auto text-center bg-gray-900"
      >
        <div class="text-gray-100 text-xl">
          <div class="p-2.5 mt-1 flex items-center">
            <i class="bi bi-app-indicator px-2 py-1 rounded-md bg-blue-600"></i>
            <h1 class="font-bold text-gray-200 text-[15px] ml-3">TailwindCSS</h1>
          </div>
          <div class="my-2 bg-gray-600 h-[1px]"></div>
        </div>
        <div
          class="p-2.5 flex items-center rounded-md px-4 duration-300 cursor-pointer bg-gray-700 text-white"
        >
        <Icon name="material-symbols:search" color="white" />     
        <input
            type="text"
            placeholder="Search"
            class="text-[15px] ml-4 w-full bg-transparent focus:outline-none"
          />
        </div>
        <NuxtLink
          to="/"
          class="p-2.5 mt-3 flex items-center rounded-md px-4 duration-300 cursor-pointer hover:bg-blue-600"
          :class="activeLink('/')"
        >
          <Icon name="iconamoon:home-fill" color="white" />
          <span class="text-[15px] ml-4 text-gray-200 font-bold">Home</span>
        </NuxtLink>
        <NuxtLink
          to="/rooms"
          class="p-2.5 mt-3 flex items-center rounded-md px-4 duration-300 cursor-pointer hover:bg-blue-600"
          :class="activeLink('/rooms')"
        >
          <Icon name="material-symbols:meeting-room" color="white" />
          <span class="text-[15px] ml-4 text-gray-200 font-bold">Rooms</span>
        </NuxtLink>
        <NuxtLink
          to="/users"
          class="p-2.5 mt-3 flex items-center rounded-md px-4 duration-300 cursor-pointer hover:bg-blue-600 text-white"
          :class="activeLink('/users')"
        >
          <Icon name="ph:user-fill" color="white" />
          <span class="text-[15px] ml-4 text-gray-200 font-bold">Users</span>
        </NuxtLink>
        <NuxtLink
          to="/reservations"
          class="p-2.5 mt-3 flex items-center rounded-md px-4 duration-300 cursor-pointer hover:bg-blue-600 text-white"
          :class="activeLink('/reservations')"
        >
          <Icon name="tabler:brand-booking" color="white" />
          <span class="text-[15px] ml-4 text-gray-200 font-bold">Reservations</span>
        </NuxtLink>
        <div class="my-4 bg-gray-600 h-[1px]"></div>
        <!-- <div
          class="p-2.5 mt-3 flex items-center rounded-md px-4 duration-300 cursor-pointer hover:bg-blue-600 text-white"
          @click="toggleDropdown"
        >
          <div class="flex justify-between w-full items-center">
            <span class="text-[15px] ml-4 text-gray-200 font-bold">Chatbox</span>
            <span class="text-sm rotate-180" id="arrow">
                <Icon name="mdi:arrow-down-bold" color="white"/>
            </span>
          </div>
        </div>
        <div
          class="text-left text-sm mt-2 w-4/5 mx-auto text-gray-200 font-bold" :class="{ submenuHidden: isSubmenuHidden }"
          id="submenu"
        >
          <h1 class="cursor-pointer p-2 hover:bg-blue-600 rounded-md mt-1">
            Social
          </h1>
          <h1 class="cursor-pointer p-2 hover:bg-blue-600 rounded-md mt-1">
            Personal
          </h1>
          <h1 class="cursor-pointer p-2 hover:bg-blue-600 rounded-md mt-1">
            Friends
          </h1>
        </div> -->
        <div
          class="p-2.5 mt-3 flex items-center rounded-md px-4 duration-300 cursor-pointer hover:bg-blue-600 text-white"
        >
          <i class="bi bi-box-arrow-in-right"></i>
          <span class="text-[15px] ml-4 text-gray-200 font-bold">Logout</span>
        </div>
      </div>
    </div>
</template>
  

<style scoped>
/* Estilos para ocultar elementos */
    .submenuHidden {
        display: none;
    }
</style>