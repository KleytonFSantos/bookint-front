<script setup lang="ts">
    type Room = {
      id: number,
      roomNumber: number;
      price: number;
      vacancy: boolean;
    }
    
    const layout = 'dashboard';
    const runtimeConfig = useRuntimeConfig()
    const { data: rooms, execute } = useFetch<Room[]>(runtimeConfig.public.apiBase + '/rooms');
    
    const deleteRoom = async (id: number) => {
      await $fetch(runtimeConfig.public.apiBase + '/rooms/' + id , {
        method: 'DELETE',
        watch: false,
        onResponse() {
          execute()
        }
      })
    }
    
</script>

<template>
  <NuxtLayout :name="layout">
    <DashboardTitle>
        Rooms
    </DashboardTitle>
    <table class="table w-full p-4 bg-white rounded-lg shadow">
      <thead>
          <tr>
              <th class="border-b-2 p-4 dark:border-dark-5 whitespace-nowrap font-normal text-gray-900">
                Room Number
              </th>
              <th class="border-b-2 p-4 dark:border-dark-5 whitespace-nowrap font-normal text-gray-900">
                Price
              </th>
              <th class="border-b-2 p-4 dark:border-dark-5 whitespace-nowrap font-normal text-gray-900">
                Vacancy
              </th>
              <th class="border-b-2 p-4 dark:border-dark-5 whitespace-nowrap font-normal text-gray-900">
                Actions
              </th>
          </tr>
      </thead>
      <tbody>
          <tr class="text-gray-700 text-center" v-for="room in rooms">
              <td class="border-b-2 p-4 dark:border-dark-5">
                {{ room.roomNumber }}
              </td>
              <td class="border-b-2 p-4 dark:border-dark-5">
                {{ room.price }}
              </td>
              <td class="border-b-2 p-4 dark:border-dark-5">
                {{ room.vacancy }}
              </td>
              <td class="border-b-2 p-4 dark:border-dark-5">
                <div class="flex items-center justify-between w-full gap-4 mt-8">
                    <button @click="deleteRoom(room.id)" type="button" class="py-2 bg-indigo-600 hover:bg-indigo-700 focus:ring-indigo-500 focus:ring-offset-indigo-200 text-white w-full transition ease-in duration-200 text-center text-base font-semibold shadow-md focus:outline-none focus:ring-2 focus:ring-offset-2  rounded-lg ">
                        <Icon name="ic:baseline-delete" color="white" />     
                    </button>
                    <button type="button" class="py-2 bg-black hover:bg-gray-100 focus:ring-indigo-500 focus:ring-offset-indigo-200 text-indigo-500 hover:text-black w-full transition ease-in duration-200 text-center text-base font-semibold shadow-md focus:outline-none focus:ring-2 focus:ring-offset-2  rounded-lg ">
                        <Icon name="ic:baseline-edit" color="white" />     
                    </button>
                </div>
              </td>
          </tr>
      </tbody>
    </table>
  </NuxtLayout>
</template>