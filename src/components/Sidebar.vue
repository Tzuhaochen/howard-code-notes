<template>
  <div class="flex h-full">
    <!-- Backdrop -->
         <!-- -->

    <div
      @click="isOpen = false"
      :class="[isOpen ? 'block' : 'hidden']"
      class="block fixed z-20 inset-0 bg-black opacity-50 transition-opacity lg:hidden"
    ></div>
    <!-- End Backdrop -->
<!-- -->
    <div
      :class="[isOpen ? 'translate-x-0 ease-out' : '-translate-x-full ease-in',
               sidebar.sidebarState.isShink ?  'sm:-translate-x-40 lg:ease-in' : 'lg:translate-x-0 lg:ease-out']"
      class="fixed z-30 inset-y-0 left-0 h-screen transition duration-50 transform bg-gray-900 overflow-y-auto lg:translate-x-0 lg:static lg:inset-0"
    >
      <button @click="sidebar.onClickShinkSidebar" class="ml-40 lg:text-white hidden lg:block">shrink</button>
      <div class="flex mt-8"
          :class="[sidebar.sidebarState.isShink ? 'justify-end' : 'item-center']">
        <div class="flex"
          >
            <span v-if="sidebar.sidebarState.isShink === false" class="mt-3 text-white text-2xl mx-2 font-semibold"
              >Howard Notes</span
            >
          </div>
        </div>
        <nav class="mt-10">
          <!--:class="[$route.name === 'UIElements' ? activeClass : inactiveClass]"-->
          <router-link
            class="flex items-center duration-200 mt-4 py-2 px-6 "
            to="/backend"
          >
            <svg
              class="h-5 w-5"
              viewBox="0 0 20 20"
              fill="none"
              xmlns="http://www.w3.org/2000/svg"
            >
              <path
                d="M5 3C3.89543 3 3 3.89543 3 5V7C3 8.10457 3.89543 9 5 9H7C8.10457 9 9 8.10457 9 7V5C9 3.89543 8.10457 3 7 3H5Z"
                fill="currentColor"
              />
              <path
                d="M5 11C3.89543 11 3 11.8954 3 13V15C3 16.1046 3.89543 17 5 17H7C8.10457 17 9 16.1046 9 15V13C9 11.8954 8.10457 11 7 11H5Z"
                fill="currentColor"
              />
              <path
                d="M11 5C11 3.89543 11.8954 3 13 3H15C16.1046 3 17 3.89543 17 5V7C17 8.10457 16.1046 9 15 9H13C11.8954 9 11 8.10457 11 7V5Z"
                fill="currentColor"
              />
              <path
                d="M11 13C11 11.8954 11.8954 11 13 11H15C16.1046 11 17 11.8954 17 13V15C17 16.1046 16.1046 17 15 17H13C11.8954 17 11 16.1046 11 15V13Z"
                fill="currentColor"
              />
            </svg>

            <span  class="mx-4">Backend</span>
          </router-link>
        </nav>
      </div>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref, reactive } from 'vue'
import { sidebar } from '@/hooks/useSidebarState'
export default defineComponent({
  setup() {
    const isOpen = ref(true)

    return {
      isOpen,
      sidebar,
      // SidebarState
    }
  },
})
</script>
