<template> 
  <div class="flex h-screen"> 
      <div class="sidebar  text-white w-72"> 
          <DashboardSidebar />        
      </div> 
      <div class="content bg-gray-200 p-6 flex-1"> 
         <DashboardContent> 
          <slot />
         </DashboardContent> 
      </div> 
  </div> 
</template>