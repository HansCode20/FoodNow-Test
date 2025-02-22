<template>
    <nav class="fixed top-0 left-0 right-0 flex items-center justify-between px-20 py-4">
      <!-- Logo -->
      <div class="flex items-center">
        <img src="../assets/img/logo.svg" alt="Logo" class="w-40">
      </div>
  
      <!-- Menu Tengah -->
      <ul class="hidden md:block md:flex space-x-6 text-white font-semibold">
        <li><a href="#" class="hover:underline">Home</a></li>
        <li><a href="#" class="hover:underline">Order</a></li>
        <li><a href="#" class="hover:underline">About</a></li>
        <li><a href="#" class="hover:underline">Blog</a></li>
        <li><a href="#" class="hover:underline">Contact Us</a></li>
      </ul>
  
      <!-- Login & Register -->
      <div class="hidden md:block md:flex items-center space-x-4">
        <a href="#" class="text-white font-semibold">Login</a>
        <a href="#" class="bg-[#e77e23] text-white px-4 py-2 rounded-full font-semibold">Register</a>
      </div>
    </nav>
  </template>
  