<script>
import logo from '../assets/logo.png'

export default {
  data() {
    return {
      logo,
      currentPage: "Home",
      navItems: ["Home", "About", "Menu", "Location", "Contact"],

      menu: [
        {
          id: 1,
          name: "Caramel Milk Tea",
          price: 5,
          image: "https://i.pinimg.com/736x/81/a4/bb/81a4bbf789dc005db307140990fcad69.jpg"
        },
        {
          id: 2,
          name: "Cookies & Cream milk Tea",
          price: 6,
          image: "https://i.pinimg.com/736x/ba/7d/3d/ba7d3d35bebf2e24aa6cc3a498d5f0ab.jpg"
        },
        {
          id: 3,
          name: "Taro Milk Tea",
          price: 6,
          image: "https://i.pinimg.com/736x/cd/1a/87/cd1a872c0861c658583d985af8133766.jpg"
        },
        {
          id: 4,
          name: "Watermelon Milk Tea",
          price: 7,
          image: "https://i.pinimg.com/736x/45/a0/bc/45a0bcd70637464416a1f72d298321ca.jpg"
        },
        {
          id: 5,
          name: "Strawberry Milk Tea",
          price: 6,
          image: "https://wellbeingbarista.com/wp-content/uploads/2023/09/strawberry_milk_tea.jpg"
        },
        {
          id: 6,
          name: "Chocolate Milk Tea",
          price: 6,
          image: "https://brewedleaflove.com/wp-content/uploads/2023/01/chocolate-milk-boba-tea-1.jpg"
        },
        {
          id: 7,
          name: "Honeydew Milk Tea",
          price: 6,
          image: "https://i.pinimg.com/1200x/e7/e5/e9/e7e5e96e6ef9a669d88a93eee512ef6d.jpg"
        },
        {
          id: 8,
          name: "Okinawa Milk Tea",
          price: 7,
          image: "https://i.pinimg.com/1200x/cc/ec/cc/cceccc62cbce0f8ca3976cfa5612bfdb.jpg"
        },
        {
          id: 9,
          name: "Matcha Milk Tea",
          price: 6,
          image: "https://i.pinimg.com/736x/2a/a7/78/2aa77892ce5f2e6051e8b0b78c45812a.jpg"
        }
      ],

      Best: [
        {
          id: 9,
          name: "Matcha Milk Tea",
          price: 6,
          image: "https://i.pinimg.com/736x/2a/a7/78/2aa77892ce5f2e6051e8b0b78c45812a.jpg"
        },
        {
          id: 6,
          name: "Chocolate Milk Tea",
          price: 6,
          image: "https://brewedleaflove.com/wp-content/uploads/2023/01/chocolate-milk-boba-tea-1.jpg"
        },
        {
          id: 2,
          name: "Cookies & Cream milk Tea",
          price: 6,
          image: "https://i.pinimg.com/736x/ba/7d/3d/ba7d3d35bebf2e24aa6cc3a498d5f0ab.jpg"
        }
      ],

      cart: [],
      contact: { name: "", email: "", message: "" },
      success: false,

      // ORDER MODAL STATE
      showModal: false,
      selectedItem: null,
      order: {
        quantity: 1,
        size: "Medium",
        notes: ""
      }
    };
  },

  methods: {
    // OPEN MODAL
    openOrder(item) {
      this.selectedItem = item;
      this.showModal = true;
    },

    // CLOSE MODAL
    closeModal() {
      this.showModal = false;
    },

    // SUBMIT ORDER
    submitOrder() {
      alert(
        `Order Confirmed!
        Item: ${this.selectedItem.name}
        Quantity: ${this.order.quantity}
        Size: ${this.order.size}`
      );

      this.showModal = false;
      this.order.quantity = 1;
      this.order.size = "Medium";
      this.order.notes = "";
    }
  }
};
</script>


<template>
  <div class="font-sans overflow-x-hidden">

    <!-- NAVBAR -->
    <nav class="fixed w-full z-50 h-28
            bg-white/10 
            backdrop-blur-xl 
            border-b border-white/20
            shadow-[0_8px_32px_rgba(0,0,0,0.15)]">

      <div class="max-w-7xl mx-auto px-4 sm:px-6 
              flex justify-between items-center h-full">

        <!-- Logo -->
        <div class="flex items-center mt-2">
          <img :src="logo" alt="Logo" class="h-20 sm:h-24 md:h-28 lg:h-32
                  w-auto object-contain brightness-90
                  transition duration-500
                  scale-125 sm:scale-140 md:scale-150 lg:scale-160
                  drop-shadow-[0_0_20px_rgba(255,105,180,0.6)]" />
        </div>

        <!-- Navigation -->
        <div class="flex gap-4 sm:gap-6 md:gap-10 
                font-medium flex-wrap justify-end">

          <button v-for="item in navItems" :key="item" @click="currentPage = item" class="relative 
                     text-sm sm:text-base md:text-lg lg:text-xl
                     text-yellow-400 tracking-wide
                     transition duration-300 group">

            <span class="group-hover:text-white transition duration-300 cursor-pointer">
              {{ item }}
            </span>

            <!-- Neon underline -->
            <span class="absolute left-0 -bottom-2 w-0 h-[3px]
                     bg-gradient-to-r from-yellow-500 to-yellow-500
                     transition-all duration-300
                     group-hover:w-full
                     shadow-[0_0_10px_rgba(255,105,180,0.8)]">
            </span>

          </button>

        </div>

      </div>
    </nav>

    <div class="pt-28">

      <!-- HOME -->
      <section v-if="currentPage === 'Home'"
        class="relative h-screen w-full overflow-hidden flex items-center justify-center">

        <!-- Background Image (Full Cover) -->
        <div class="absolute inset-0">
          <img src="https://i.pinimg.com/736x/bb/e6/69/bbe669f625e055e9ac99ec22d4c3ae5e.jpg" alt="Milk Tea Background"
            class="w-full h-full object-cover brightness-50" />
        </div>

        <!-- Content -->
        <div class="ml-0 sm:ml-10 md:ml-20 lg:ml-40 px-4 sm:px-6">
          <div class="relative z-10 text-center max-w-4xl animate-slide">

            <h2 class="text-4xl sm:text-5xl md:text-6xl lg:text-8xl font-semibold
        bg-clip-text text-transparent 
        bg-yellow-400/100 
        mb-6">
              Fresh & Creamy <br> Milk Tea <span class="text-white">🧋</span>
            </h2>

            <p class="text-base sm:text-lg md:text-xl lg:text-2xl text-white mb-8 drop-shadow-lg">
              Experience the perfect blend of tea, milk, and chewy pearls <br> made fresh every day.
              Taste happiness in every sip!
            </p>

            <button @click="currentPage = 'Menu'" class="bg-yellow-600 text-white 
        px-6 sm:px-8 py-2 sm:py-3 rounded-full
        hover:scale-110 duration-300 cursor-pointer">
              Explore Menu
            </button>

          </div>
        </div>

      </section>

      <!-- ABOUT -->
      <section v-if="currentPage === 'About'" class="py-12 sm:py-16 md:py-20 bg-blue-600">

        <div class="max-w-6xl mx-auto px-4 sm:px-6">

          <!-- Title -->
          <div class="text-center mb-10 sm:mb-14">
            <h2 class="text-2xl sm:text-4xl md:text-5xl font-extrabold text-yellow-500 mb-6">
              About Rheanie Milk Tea 🧋
            </h2>
            <p class="text-white/90 text-base sm:text-lg max-w-3xl mx-auto leading-relaxed">
              Rheanie Milk Tea started with a passion for crafting high-quality drinks.
              From classic brown sugar milk tea to fruity refreshers,
              we use premium ingredients and fresh pearls every single day.
            </p>
          </div>

          <!-- Modern Content Layout -->
          <div class="grid grid-cols-1 md:grid-cols-2 gap-8 md:gap-12 items-center mb-12 md:mb-16">

            <!-- Image -->
            <div class="relative group">
              <img src="https://i.pinimg.com/736x/e4/46/a8/e446a87967458c363eda5b94d41e312d.jpg" class="rounded-3xl shadow-2xl w-full h-64 sm:h-80 md:h-[400px] object-cover 
                 group-hover:scale-105 transition duration-500" />
              <div class="absolute inset-0 bg-black/20 rounded-3xl"></div>
            </div>

            <!-- Text -->
            <div class="space-y-6 text-white text-center md:text-left">
              <h3 class="text-2xl sm:text-3xl font-bold">Crafted With Love ❤️</h3>
              <p class="text-base sm:text-lg leading-relaxed">
                Every cup is carefully prepared to bring joy in every sip.
                We believe milk tea is more than just a drink —
                it's an experience shared with friends and family.
              </p>

              <div class="flex flex-col sm:flex-row gap-6 pt-4 justify-center md:justify-start">
                <div>
                  <h4 class="text-3xl sm:text-4xl font-bold">100%</h4>
                  <p class="text-sm">Fresh Ingredients</p>
                </div>
                <div>
                  <h4 class="text-3xl sm:text-4xl font-bold">5★</h4>
                  <p class="text-sm">Customer Rating</p>
                </div>
              </div>
            </div>

          </div>

          <!-- Feature Cards -->
          <div class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 gap-6 md:gap-8">

            <!-- Card 1 -->
            <div
              class="bg-white/80 backdrop-blur-lg rounded-2xl shadow-xl p-6 text-center hover:scale-105 transition duration-300">
              <img src="https://i.pinimg.com/736x/5a/22/1c/5a221c2370d43ef30383704d7577d7f9.jpg"
                class="h-40 w-full object-cover rounded-xl mb-4" />
              <h4 class="text-lg sm:text-xl font-semibold text-yellow-500 mb-2">Premium Tea</h4>
              <p class="text-gray-600 text-sm">
                We use high-quality tea leaves for rich and authentic flavors.
              </p>
            </div>

            <!-- Card 2 -->
            <div
              class="bg-white/80 backdrop-blur-lg rounded-2xl shadow-xl p-6 text-center hover:scale-105 transition duration-300">
              <img src="https://i.pinimg.com/736x/67/97/41/679741f96f7d7a5a3cdf7027a43d2202.jpg"
                class="h-40 w-full object-cover rounded-xl mb-4" />
              <h4 class="text-lg sm:text-xl font-semibold text-yellow-500 mb-2">Fresh Pearls</h4>
              <p class="text-gray-600 text-sm">
                Soft, chewy tapioca pearls cooked fresh daily.
              </p>
            </div>

            <!-- Card 3 -->
            <div
              class="bg-white/80 backdrop-blur-lg rounded-2xl shadow-xl p-6 text-center hover:scale-105 transition duration-300">
              <img src="https://i.pinimg.com/736x/99/64/f1/9964f10f94e329fdd5caf518031906d9.jpg"
                class="h-40 w-full object-cover rounded-xl mb-4" />
              <h4 class="text-lg sm:text-xl font-semibold text-yellow-500 mb-2">Cozy Place</h4>
              <p class="text-gray-600 text-sm">
                A warm and welcoming space to enjoy your favorite drinks.
              </p>
            </div>

          </div>

        </div>
      </section>




      <!-- ================= MENU ================= -->
      <section v-if="currentPage === 'Menu'" class="py-12 sm:py-16 md:py-20">

        <h2 class="text-2xl sm:text-3xl md:text-4xl font-bold text-center text-yellow-500 mb-10 sm:mb-16">
          Our Menu
        </h2>

        <!-- MENU GRID -->
        <div class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 
              gap-6 sm:gap-8 
              max-w-6xl mx-auto px-4 sm:px-6">

          <div v-for="item in menu" :key="item.id" class="bg-pink-200 shadow-md rounded-xl p-4 sm:p-6 text-center">

            <!-- IMAGE (NOT CHANGED) -->
            <img :src="item.image" @click="openOrder(item)"
              class="w-full h-56 sm:h-60 md:h-64 object-cover rounded-lg mb-4 cursor-pointer hover:scale-105 transition duration-300" />

            <h3 class="text-lg sm:text-xl font-semibold text-yellow-500 mb-2">
              {{ item.name }}
            </h3>

            <p class="text-gray-700 text-base sm:text-lg font-medium">
              ${{ item.price }}
            </p>

          </div>
        </div>

        <h2 class="text-2xl sm:text-3xl md:text-4xl font-bold text-center text-yellow-500 my-14 sm:my-20">
          Our Best Seller!
        </h2>

        <div class="grid grid-cols-1 sm:grid-cols-2 md:grid-cols-3 
              gap-6 sm:gap-8 
              max-w-6xl mx-auto px-4 sm:px-6">

          <div v-for="item in Best" :key="item.id"
            class="bg-pink-200 shadow-md rounded-xl p-4 sm:p-6 text-center relative">

            <!-- Badge -->
            <span class="absolute top-3 right-3 sm:top-4 sm:right-4 
                   bg-yellow-400 text-white text-xs px-3 py-1 rounded-full">
              ⭐ Best Seller
            </span>

            <!-- IMAGE (UNCHANGED) -->
            <img :src="item.image" @click="openOrder(item)"
              class="w-full h-56 sm:h-60 md:h-64 object-cover rounded-lg mb-4 cursor-pointer transition duration-300" />

            <h3 class="text-lg sm:text-xl font-semibold text-yellow-500 mb-2">
              {{ item.name }}
            </h3>

            <p class="text-gray-700 text-base sm:text-lg font-medium">
              ${{ item.price }}
            </p>

          </div>

        </div>

      </section>

      <!-- ================= LOCATION ================= -->
      <section v-if="currentPage === 'Location'" class="py-12 sm:py-16 md:py-20 bg-blue-600">

        <h2 class="text-2xl sm:text-3xl md:text-4xl font-bold text-center text-yellow-500 mb-10 sm:mb-16">
          Visit Our Store
        </h2>

        <div class="max-w-6xl mx-auto px-4 sm:px-6 
              grid grid-cols-1 md:grid-cols-2 
              gap-8 sm:gap-10 items-center">

          <!-- LEFT SIDE (INFO) -->
          <div class="space-y-6 text-center md:text-left">

            <div>
              <h3 class="text-xl sm:text-2xl font-semibold text-yellow-500 mb-2">📍 Address</h3>
              <p class="text-white text-sm sm:text-base">
                Roxas Street <br>
                Tagum City, Davao del Norte
              </p>
            </div>

            <div>
              <h3 class="text-xl sm:text-2xl font-semibold text-yellow-500 mb-2">⏰ Opening Hours</h3>
              <p class="text-white text-sm sm:text-base">
                Monday – Friday: 10:00 AM – 9:00 PM <br>
                Saturday – Sunday: 11:00 AM – 10:00 PM
              </p>
            </div>

            <div>
              <h3 class="text-xl sm:text-2xl font-semibold text-yellow-500 mb-2">📞 Contact</h3>
              <p class="text-white text-sm sm:text-base break-words">
                Phone: 0912 345 6789 <br>
                Email: support@milkteashop.com
              </p>
            </div>

          </div>

          <!-- RIGHT SIDE (MAP) -->
          <div class="w-full h-64 sm:h-80 md:h-96 rounded-2xl overflow-hidden shadow-lg">

            <iframe class="w-full h-full" src="https://maps.google.com/maps?q=7.4498699,125.8035451&z=17&output=embed"
              loading="lazy" allowfullscreen>
            </iframe>

          </div>

        </div>

      </section>

      <!-- ================= ORDER MODAL ================= -->
      <div v-if="showModal" class="fixed inset-0 bg-black/50 backdrop-blur-sm 
            flex items-center justify-center 
            z-50 px-4 sm:px-6">

        <div class="bg-white w-full max-w-md 
              rounded-2xl p-4 sm:p-6 
              relative shadow-2xl
              max-h-[90vh] overflow-y-auto">

          <!-- CLOSE BUTTON -->
          <button @click="closeModal" class="absolute top-3 right-4 
                   text-lg sm:text-xl font-bold 
                   text-gray-600 hover:text-red-500">
            ✕
          </button>

          <h2 class="text-xl sm:text-2xl font-bold text-yellow-500 mb-4 text-center">
            Order {{ selectedItem?.name }}
          </h2>

          <!-- SAME IMAGE (NOT CHANGED) -->
          <img :src="selectedItem?.image" class="w-full h-40 sm:h-48 object-cover rounded-xl mb-4" />

          <form @submit.prevent="submitOrder" class="space-y-3 sm:space-y-4">

            <!-- Quantity -->
            <div>
              <label class="text-sm font-medium text-gray-700">Quantity</label>
              <input type="number" v-model="order.quantity" min="1" class="w-full px-3 py-2 rounded-lg border 
                 focus:ring-2 focus:ring-pink-400 
                 outline-none text-gray-700 text-sm sm:text-base">
            </div>

            <!-- Size -->
            <div>
              <label class="text-sm font-medium text-gray-700">Size</label>
              <select v-model="order.size" class="w-full px-3 py-2 rounded-lg border 
                 focus:ring-2 focus:ring-pink-400 
                 outline-none text-gray-700 text-sm sm:text-base">
                <option>Small</option>
                <option>Medium</option>
                <option>Large</option>
              </select>
            </div>

            <!-- Submit -->
            <button type="submit" class="w-full bg-pink-500 text-white py-2 sm:py-3 
               rounded-lg hover:bg-pink-600 transition text-sm sm:text-base">
              Confirm Order
            </button>

          </form>
        </div>
      </div>



      <!-- CONTACT -->
      <section v-if="currentPage === 'Contact'" class="py-12 sm:py-16 md:py-20 bg-blue-600">
        <div class="max-w-6xl mx-auto px-4 sm:px-6">

          <h2 class="text-2xl sm:text-3xl md:text-4xl font-bold text-center text-yellow-500 mb-10 sm:mb-12">
            Contact Us
          </h2>

          <div class="grid grid-cols-1 md:grid-cols-2 gap-8 sm:gap-12 items-start">

            <!-- LEFT SIDE - CONTACT INFO -->
            <div class="bg-white/60 backdrop-blur-lg p-6 sm:p-8 rounded-2xl shadow-lg space-y-6">

              <h3 class="text-xl sm:text-2xl font-semibold text-yellow-500 mb-4">
                Get In Touch
              </h3>

              <div class="flex items-start gap-3 sm:gap-4">
                <div class="text-xl sm:text-2xl">📍</div>
                <div>
                  <p class="font-semibold text-gray-800 text-sm sm:text-base">Address</p>
                  <p class="text-gray-600 text-sm break-words">
                    Roxas Street <br>
                    Tagum City, Davao del Norte
                  </p>
                </div>
              </div>

              <div class="flex items-start gap-3 sm:gap-4">
                <div class="text-xl sm:text-2xl">📞</div>
                <div>
                  <p class="font-semibold text-gray-800 text-sm sm:text-base">Phone</p>
                  <p class="text-gray-600 text-sm break-words">
                    +63 970 029 9688
                  </p>
                </div>
              </div>

              <div class="flex items-start gap-3 sm:gap-4">
                <div class="text-xl sm:text-2xl">✉️</div>
                <div>
                  <p class="font-semibold text-gray-800 text-sm sm:text-base">Email</p>
                  <p class="text-gray-600 text-sm break-words">
                    rheaniemilktea@email.com
                  </p>
                </div>
              </div>

              <div class="pt-4 border-t">
                <p class="text-xs sm:text-sm text-gray-500">
                  We usually respond within a few hours during business days.
                </p>
              </div>

            </div>

            <!-- RIGHT SIDE - FORM -->
            <div class="bg-white/60 backdrop-blur-lg p-6 sm:p-8 rounded-2xl shadow-xl">

              <form @submit.prevent="submitForm" class="space-y-3 sm:space-y-4">

                <input v-model="contact.name" type="text" required placeholder="Your Name"
                  class="w-full border border-gray-300 p-2.5 sm:p-3 text-sm sm:text-base text-gray-700 rounded-lg focus:ring-2 focus:ring-yellow-500 focus:outline-none" />

                <input v-model="contact.email" type="email" required placeholder="Your Email"
                  class="w-full border border-gray-300 p-2.5 sm:p-3 text-sm sm:text-base text-gray-700 rounded-lg focus:ring-2 focus:ring-yellow-500 focus:outline-none" />

                <textarea v-model="contact.message" required placeholder="Your Message"
                  class="w-full border border-gray-300 p-2.5 sm:p-3 text-sm sm:text-base text-gray-700 rounded-lg h-28 sm:h-32 resize-none focus:ring-2 focus:ring-yellow-500 focus:outline-none"></textarea>

                <button
                  class="w-full bg-yellow-600 text-white py-2.5 sm:py-3 text-sm sm:text-base rounded-lg font-semibold hover:scale-[1.02] transition-all duration-300 shadow-md">
                  Send Message
                </button>

                <p v-if="success" class="text-green-600 text-center font-medium text-sm sm:text-base">
                  Message sent successfully!
                </p>

              </form>

            </div>

          </div>
        </div>
      </section>

    </div>
  </div>
  <!-- ================= FOOTER ================= -->
  <footer class="relative bg-gradient-to-r from-pink-200/70 via-green-200/60 to-pink-200/70 
         backdrop-blur-xl border-t border-white/40 
         text-gray-800 pt-10 sm:pt-12 pb-6 mt-16 sm:mt-20">

    <div class="max-w-7xl mx-auto px-4 sm:px-6 
              grid grid-cols-1 sm:grid-cols-2 md:grid-cols-4 
              gap-8 sm:gap-10">

      <!-- Brand -->
      <div>
        <h2 class="text-xl sm:text-2xl font-extrabold bg-yellow-200 
             bg-clip-text text-transparent mb-4">
          Rheanie Milk Tea
        </h2>
        <p class="text-sm text-gray-700 leading-relaxed">
          Serving happiness in every sip 🧋
          Freshly brewed tea, creamy milk, and chewy pearls made with love.
        </p>
      </div>

      <!-- Quick Links -->
      <div>
        <h3 class="font-semibold text-base sm:text-lg mb-4 text-yellow-200">Quick Links</h3>
        <ul class="space-y-2 text-sm">
          <li><button @click="currentPage = 'Home'" class="hover:text-pink-500 transition">Home</button></li>
          <li><button @click="currentPage = 'Menu'" class="hover:text-pink-500 transition">Menu</button></li>
          <li><button @click="currentPage = 'About'" class="hover:text-pink-500 transition">About</button></li>
          <li><button @click="currentPage = 'Location'" class="hover:text-pink-500 transition">Location</button></li>
        </ul>
      </div>

      <!-- Contact Info + Map -->
      <div class="sm:col-span-2 md:col-span-2">
        <h3 class="font-semibold text-base sm:text-lg mb-4 text-yellow-200">Contact Us</h3>
        <ul class="space-y-2 text-sm mb-4 break-words">
          <li>📍 Roxas Street, Tagum City, Davao del Norte</li>
          <li>📞 +63 970 029 9688</li>
          <li>✉️ rheaniemilktea@email.com</li>
        </ul>

        <div class="rounded-xl overflow-hidden shadow-md">
          <iframe src="https://maps.google.com/maps?q=7.4498699,125.8035451&z=17&output=embed"
            class="w-full h-28 sm:h-32 border-0" loading="lazy" allowfullscreen>
          </iframe>
        </div>
      </div>

    </div>

    <!-- Bottom -->
    <div class="border-t border-white/40 mt-8 sm:mt-10 pt-4 text-center text-xs sm:text-sm text-gray-600">
      © {{ new Date().getFullYear() }} Rheanie Milk Tea. All Rights Reserved.
    </div>

  </footer>
</template>
