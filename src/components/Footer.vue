<template>
    <footer class="bg-white border-t border-gray-200 py-10 mt-20">
      <div class="container mx-auto grid grid-cols-1 md:grid-cols-4 gap-8 px-6">
        <!-- Logo dan Social Media -->
        <div>
          <h2 class="text-4xl font-bold text-orange-500">
            Food<span class="text-gray-800">now</span>
          </h2>
          <p class="mt-4 font-semibold text-gray-800">Find Us :</p>
          <div class="flex space-x-4 mt-2">
            <a href="#" aria-label="Facebook" class="text-orange-500 border border-orange-500 rounded-full p-2 hover:bg-orange-500 hover:text-white">
              <img src="../assets/img/icons/facebook.svg" alt="Facebook Icon" class="w-6 h-6" />
            </a>
            <a href="#" aria-label="Instagram" class="text-orange-500 border border-orange-500 rounded-full p-2 hover:bg-orange-500 hover:text-white">
              <img src="../assets/img/icons/instagram.svg" alt="Instagram Icon" class="w-6 h-6" />
            </a>
            <a href="#" aria-label="YouTube" class="text-orange-500 border border-orange-500 rounded-full p-2 hover:bg-orange-500 hover:text-white">
              <img src="../assets/img/icons/youtube.svg" alt="YouTube Icon" class="w-6 h-6" />
            </a>
          </div>
        </div>
  
        <!-- Navigation -->
        <div>
          <h3 class="text-xl font-semibold text-orange-500">Navigation</h3>
          <div class="flex items-start gap-6 mt-4 text-gray-800">
            <ul class="space-y-5">
              <li><a href="#" class="hover:text-orange-500">Home</a></li>
              <li><a href="#" class="hover:text-orange-500">Order</a></li>
              <li><a href="#" class="hover:text-orange-500">About</a></li>
              <li><a href="#" class="hover:text-orange-500">Blog</a></li>
            </ul>
            <ul class="space-y-5">
              <li><a href="#" class="hover:text-orange-500">Contact</a></li>
              <li><a href="#" class="hover:text-orange-500">Login</a></li>
              <li><a href="#" class="hover:text-orange-500">Register</a></li>
            </ul>
          </div>
        </div>
  
        <!-- Contact -->
        <div>
          <h3 class="text-xl font-semibold text-orange-500">Contact</h3>
          <ul class="mt-4 space-y-3 text-gray-800">
            <li class="flex items-center gap-2">
              <img src="../assets/img/icons/mail.svg" alt="Email Icon" class="w-6 h-6" />
              <a href="mailto:Food.now@mail.com" class="hover:text-orange-500">Food.now@mail.com</a>
            </li>
            <li class="flex items-center gap-2">
              <img src="../assets/img/icons/phone.svg" alt="Phone Icon" class="w-6 h-6" />
              <a href="tel:+62848477102943" class="hover:text-orange-500">+62848477102943</a>
            </li>
            <li class="flex items-center gap-2">
              <img src="../assets/img/icons/whatsapp.svg" alt="WhatsApp Icon" class="w-6 h-6" />
              <a href="https://wa.me/628184938494" target="_blank" rel="noopener noreferrer" class="hover:text-orange-500">+628184938494</a>
            </li>
          </ul>
        </div>
  
        <!-- Location -->
        <div>
          <h3 class="text-xl font-semibold text-orange-500">Location</h3>
          <div class="flex items-center gap-1 mt-4">
            <img src="../assets/img/icons/location.svg" alt="Location Icon" class="w-6 h-6" />
            <p class="font-bold text-lg">Kerobokan</p>
          </div>
          <p class="text-gray-800 mt-2 ml-6">
            Jl. Raya Kerobokan Br Taman, Kuta No.98,<br />
            Kerobokan Kelod, Kec. Kuta Utara,<br />
            Kabupaten Badung, Bali 80361
          </p>
        </div>
      </div>
  
      <!-- Copyright -->
      <div class="text-left md:text-center px-10 text-gray-600 text-sm mt-8">
        <p>
          Copyright © 2022 Foodnow. All Rights Reserved.
          Powered by PT. Timedoor Indonesia. |
          <a href="#" class="hover:underline">Privacy Policy</a>
        </p>
        <p class="mt-2">
          This site is protected by reCAPTCHA and the Google
          <a href="#" class="hover:underline">Privacy Policy</a> and
          <a href="#" class="hover:underline">Terms of Service</a> apply.
        </p>
      </div>
    </footer>
  </template>

  