<template>
  <div class="modal-container">
    <div class="image">
      <div class="pt-10 pb-10">
        <div
          class="bg-white shadow-lg rounded-md px-6 py-4 max-w-[34rem] mx-0 md:mx-[10%]"
        >
          <p class="text-3xl font-semibold">Book a Ride</p>
          <form class="max-w-lg w-full mt-6">
            <div class="relative">
              <label
                class="label left-2 top-2 pt-0 text-sm font-medium text-black ml-1 dark:text-white pointer-events-none"
                >Ride type</label
              >
              <select
                id="countries"
                class="pb-2 pt-4 bg-gray-100 text-gray-900 text-md font-medium rounded-md focus:ring-black focus:border-black block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-600 dark:text-white dark:focus:ring-black dark:focus:border-black"
                required
              >
                <option class="font-medium text-base mt-3" value="#">
                  Airport Pickup
                </option>
                <option class="font-medium text-base" value="#">
                  Airport Drop-off
                </option>
                <option class="font-medium text-base" value="#">
                  For a Day
                </option>
                <option class="font-medium text-base" value="#">
                  By Hours
                </option>
              </select>
            </div>
            <div class="flex items-center mb-4 mt-4">
              <input
                id="default-checkbox"
                type="checkbox"
                value=""
                class="appearance-none w-4 h-4 bg-[#F1F1F1] checked:bg-[black] rounded p-[10px] cursor-pointer"
                required
              />
              <label
                for="default-checkbox"
                class="ms-2 text-md font-medium text-gray-900 dark:text-gray-500"
                >This ride book for another person</label
              >
            </div>

            <div class="relative">
              <label
                class="label left-2 top-2 pt-0 text-sm font-medium text-black ml-1 dark:text-white pointer-events-none"
                >From</label
              >
              <select
                id="countries"
                class="pb-2 pt-4 bg-gray-100 text-gray-900 text-md font-medium rounded-md focus:ring-black focus:border-black block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-600 dark:text-white dark:focus:ring-black dark:focus:border-black"
                re
              >
                <option disabled selected value="" class="font-thin text-base">
                  Select an option
                </option>
                <option
                  class="font-medium text-base mt-3 option-lines"
                  value="#"
                >
                  Riyadh (RUH) King Fahd International Airport
                </option>

                <option class="font-medium text-base option-lines" value="#">
                  Jeddah (JED) King Abdulaziz International Airport
                </option>
                <option class="font-medium text-base option-lines" value="#">
                  Dammam (DMM) King Fahd International Airport Dammam
                </option>
              </select>
            </div>

            <div>
              <div class="relative">
                <label
                  class="label left-2 top-2 pt-1 text-sm font-medium text-black ml-1 dark:text-white pointer-events-none"
                  >To</label
                >
                <p
                  class="label left-2 top-2 pt-5 text-sm font-medium text-black ml-1 dark:text-white pointer-events-none"
                >
                  Al Thoumamah Rd, An Narjis, Uthman ..
                </p>
                <input
                  type="text"
                  id="first_name"
                  class="mt-5 bg-gray-100 text-black text-sm rounded-lg block w-full p-2.5 pt-5"
                  required
                />
                <img
                  @click="openModal"
                  class="map pt-5 cursor-pointer"
                  src="../assets/Map pin.png"
                />
              </div>

              <div class="relative">
                <div
                  v-if="isModalOpen"
                  class="fixed inset-0 flex items-center justify-center bg-black bg-opacity-[0.1]"
                >
                  <div class="bg-white rounded-lg p-8 ml-10 popup">
                    <img
                      src="../assets/close.png"
                      class="close"
                      @click="closeModal"
                    />
                    <div>
                      <h1 class="text-xl font-bold">Select Pickup location</h1>
                    </div>
                    <div class="mt-3">
                      <img src="../assets/image2.png" class="photo" />
                    </div>
                    <div class="absolute">
                      <img src="../assets/Map pin.png" class="pin" />
                      <p
                        class="cont left-2 top-2 pb-2 text-sm font-medium text-black ml-1 dark:text-white pointer-events-none"
                      >
                        6995 Uthman Ibn Affan Rd, 4636, An Narjis, Riyadh 13324
                      </p>
                      <input
                        type="text"
                        id="first_name"
                        class="input mt-5 bg-white text-black text-sm rounded-lg block w-full p-2.5"
                        required
                      />
                    </div>
                    <button
                      class="btn w-full bg-black text-white p-2 rounded-md mt-2"
                    >
                      Select
                    </button>
                  </div>
                </div>
              </div>

              <div class="relative">
                <div
                  class="absolute inset-y-0 end-0 top-0 flex items-center pe-3.5 pointer-events-none"
                ></div>
                <input
                  type="datetime-local"
                  class="mt-5 bg-gray-100 text-black text-sm rounded-lg block w-full p-2.5 pt-3"
                  min="09:00"
                  max="10:00"
                  value="00:00"
                  required
                />
              </div>
            </div>
            <div class="relative">
              <input
                type="text"
                id=""
                class="mt-5 mb-5 pb-3 pt-4 bg-gray-100 text-black text-sm rounded-lg block w-full p-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white"
                placeholder="Enter flight number"
                required
              />
              <label
                class="label left-2 top-2 pt-0 text-sm font-medium text-gray-900 dark:text-white pointer-events-none"
                >Flight number</label
              >
            </div>
            <div>
              <div class="flex justify-between">
                <h1 class="text-lg font-semibold mb-3">Select car class</h1>
              </div>
              <Swiper
                :slides-per-view="2"
                :space-between="-1"
                :modules="modules"
                class="mySwiper"
                :navigation="{
                  nextEl: '.swiper-button-next',
                  prevEl: '.swiper-button-prev',
                }"
              >
                <SwiperSlide>
                  <div
                    class="card p-6 bg-white border border-gray-200 rounded-lg shadow dark:bg-gray-800 dark:border-gray-700"
                  >
                    <img src="../assets/car.png" class="w-full" />
                    <h5
                      class="text-md font-bold tracking-tight text-gray-900 dark:text-white"
                    >
                      Pure class
                    </h5>
                    <p class="text-sm mb-2">Lucid Air Dream</p>

                    <div class="gap-2">
                      <img src="../assets/2 User.png" />
                      <p
                        class="text-sm font-medium pr-7"
                        style="margin-top: -17px; margin-left: 26px"
                      >
                        x2
                      </p>
                      <div class="justify-between gap-2">
                        <img
                          src="../assets/Bag 2.png"
                          style="margin-top: -14px; margin-left: 62px"
                        />
                        <p
                          class="text-sm font-medium pr-7"
                          style="margin-top: -17px; margin-left: 87px"
                        >
                          x2
                        </p>
                      </div>
                    </div>
                    <div class="flex gap-2 mt-9">
                      <p class="text-md font-bold">SAR</p>
                      <p class="text-md font-bold">850.50</p>
                    </div>
                  </div>
                </SwiperSlide>
                <SwiperSlide>
                  <div
                    class="card p-6 bg-white border-4 border-black rounded-lg shadow dark:bg-gray-800 dark:border-gray-700"
                  >
                    <img src="../assets/car2.png" class="w-full" />
                    <h5
                      class="text-md font-bold tracking-tight text-gray-900 dark:text-white"
                    >
                      Business Class
                    </h5>
                    <p class="text-sm mb-2">Lucid Air Dream</p>
                    <div class="gap-2">
                      <img src="../assets/2 User.png" />
                      <p
                        class="text-sm font-medium pr-7"
                        style="margin-top: -17px; margin-left: 26px"
                      >
                        x2
                      </p>
                      <div class="justify-between gap-2">
                        <img
                          src="../assets/Bag 2.png"
                          style="margin-top: -14px; margin-left: 62px"
                        />
                        <p
                          class="text-sm font-medium pr-7"
                          style="margin-top: -17px; margin-left: 87px"
                        >
                          x2
                        </p>
                      </div>
                    </div>

                    <div class="flex gap-2 mt-5">
                      <p class="text-md font-bold">SAR</p>
                      <p class="text-md font-bold">240.00</p>
                    </div>
                  </div>
                </SwiperSlide>

                <SwiperSlide>
                  <div
                    class="card p-6 bg-white border border-gray-200 rounded-lg shadow dark:bg-gray-800 dark:border-gray-700"
                  >
                    <img src="../assets/car.png" class="w-full" />
                    <h5
                      class="text-md font-bold tracking-tight text-gray-900 dark:text-white"
                    >
                      Pure class
                    </h5>
                    <p class="text-sm mb-2">Lucid Air Dream</p>

                    <div class="gap-2">
                      <img src="../assets/2 User.png" />
                      <p
                        class="text-sm font-medium pr-7"
                        style="margin-top: -17px; margin-left: 26px"
                      >
                        x2
                      </p>
                      <div class="justify-between gap-2">
                        <img
                          src="../assets/Bag 2.png"
                          style="margin-top: -14px; margin-left: 62px"
                        />
                        <p
                          class="text-sm font-medium pr-7"
                          style="margin-top: -17px; margin-left: 87px"
                        >
                          x2
                        </p>
                      </div>
                    </div>
                    <div class="flex gap-2 mt-9">
                      <p class="text-md font-bold">SAR</p>
                      <p class="text-md font-bold">850.50</p>
                    </div>
                  </div>
                </SwiperSlide>
                <SwiperSlide>
                  <div
                    class="card p-6 bg-white border-4 border-black rounded-lg shadow dark:bg-gray-800 dark:border-gray-700"
                  >
                    <img src="../assets/car2.png" class="w-full" />
                    <h5
                      class="text-md font-bold tracking-tight text-gray-900 dark:text-white"
                    >
                      Business Class
                    </h5>
                    <p class="text-sm mb-2">Lucid Air Dream</p>
                    <div class="gap-2">
                      <img src="../assets/2 User.png" />
                      <p
                        class="text-sm font-medium pr-7"
                        style="margin-top: -17px; margin-left: 26px"
                      >
                        x2
                      </p>
                      <div class="justify-between gap-2">
                        <img
                          src="../assets/Bag 2.png"
                          style="margin-top: -14px; margin-left: 62px"
                        />
                        <p
                          class="text-sm font-medium pr-7"
                          style="margin-top: -17px; margin-left: 87px"
                        >
                          x2
                        </p>
                      </div>
                    </div>

                    <div class="flex gap-2 mt-5">
                      <p class="text-md font-bold">SAR</p>
                      <p class="text-md font-bold">240.00</p>
                    </div>
                  </div>
                </SwiperSlide>

                <SwiperSlide>
                  <div
                    class="card p-6 bg-white border border-gray-200 rounded-lg shadow dark:bg-gray-800 dark:border-gray-700"
                  >
                    <img src="../assets/car.png" class="w-full" />
                    <h5
                      class="text-md font-bold tracking-tight text-gray-900 dark:text-white"
                    >
                      Pure class
                    </h5>
                    <p class="text-sm mb-2">Lucid Air Dream</p>

                    <div class="gap-2">
                      <img src="../assets/2 User.png" />
                      <p
                        class="text-sm font-medium pr-7"
                        style="margin-top: -17px; margin-left: 26px"
                      >
                        x2
                      </p>
                      <div class="justify-between gap-2">
                        <img
                          src="../assets/Bag 2.png"
                          style="margin-top: -14px; margin-left: 62px"
                        />
                        <p
                          class="text-sm font-medium pr-7"
                          style="margin-top: -17px; margin-left: 87px"
                        >
                          x2
                        </p>
                      </div>
                    </div>
                    <div class="flex gap-2 mt-9">
                      <p class="text-md font-bold">SAR</p>
                      <p class="text-md font-bold">850.50</p>
                    </div>
                  </div>
                </SwiperSlide>
                <SwiperSlide>
                  <div
                    class="card p-6 bg-white border-4 border-black rounded-lg shadow dark:bg-gray-800 dark:border-gray-700"
                  >
                    <img src="../assets/car2.png" class="w-full" />
                    <h5
                      class="text-md font-bold tracking-tight text-gray-900 dark:text-white"
                    >
                      Business Class
                    </h5>
                    <p class="text-sm mb-2">Lucid Air Dream</p>
                    <div class="gap-2">
                      <img src="../assets/2 User.png" />
                      <p
                        class="text-sm font-medium pr-7"
                        style="margin-top: -17px; margin-left: 26px"
                      >
                        x2
                      </p>
                      <div class="justify-between gap-2">
                        <img
                          src="../assets/Bag 2.png"
                          style="margin-top: -14px; margin-left: 62px"
                        />
                        <p
                          class="text-sm font-medium pr-7"
                          style="margin-top: -17px; margin-left: 87px"
                        >
                          x2
                        </p>
                      </div>
                    </div>

                    <div class="flex gap-2 mt-5">
                      <p class="text-md font-bold">SAR</p>
                      <p class="text-md font-bold">240.00</p>
                    </div>
                  </div>
                </SwiperSlide>

                <SwiperSlide>
                  <div
                    class="card p-6 bg-white border border-gray-200 rounded-lg shadow dark:bg-gray-800 dark:border-gray-700"
                  >
                    <img src="../assets/car.png" class="w-full" />
                    <h5
                      class="text-md font-bold tracking-tight text-gray-900 dark:text-white"
                    >
                      Pure class
                    </h5>
                    <p class="text-sm mb-2">Lucid Air Dream</p>

                    <div class="gap-2">
                      <img src="../assets/2 User.png" />
                      <p
                        class="text-sm font-medium pr-7"
                        style="margin-top: -17px; margin-left: 26px"
                      >
                        x2
                      </p>
                      <div class="justify-between gap-2">
                        <img
                          src="../assets/Bag 2.png"
                          style="margin-top: -14px; margin-left: 62px"
                        />
                        <p
                          class="text-sm font-medium pr-7"
                          style="margin-top: -17px; margin-left: 87px"
                        >
                          x2
                        </p>
                      </div>
                    </div>
                    <div class="flex gap-2 mt-9">
                      <p class="text-md font-bold">SAR</p>
                      <p class="text-md font-bold">850.50</p>
                    </div>
                  </div>
                </SwiperSlide>
                <SwiperSlide>
                  <div
                    class="card p-6 bg-white border-4 border-black rounded-lg shadow dark:bg-gray-800 dark:border-gray-700"
                  >
                    <img src="../assets/car2.png" class="w-full" />
                    <h5
                      class="text-md font-bold tracking-tight text-gray-900 dark:text-white"
                    >
                      Business Class
                    </h5>
                    <p class="text-sm mb-2">Lucid Air Dream</p>
                    <div class="gap-2">
                      <img src="../assets/2 User.png" />
                      <p
                        class="text-sm font-medium pr-7"
                        style="margin-top: -17px; margin-left: 26px"
                      >
                        x2
                      </p>
                      <div class="justify-between gap-2">
                        <img
                          src="../assets/Bag 2.png"
                          style="margin-top: -14px; margin-left: 62px"
                        />
                        <p
                          class="text-sm font-medium pr-7"
                          style="margin-top: -17px; margin-left: 87px"
                        >
                          x2
                        </p>
                      </div>
                    </div>

                    <div class="flex gap-2 mt-5">
                      <p class="text-md font-bold">SAR</p>
                      <p class="text-md font-bold">240.00</p>
                    </div>
                  </div>
                </SwiperSlide>
              </Swiper>
              <div class="swiper-button-prev">
                  <img
                    src="../assets/Stroke 2.png"
                    style="
                      position: relative;
                      top: -9px;
                      left: 237px;
                    "
                  />
                </div>
                <div class="swiper-button-next">
                  <img
                    src="../assets/Stroke 1.png"
                    style="
                      position: relative;
                      top: 84px;
                    "
                  />
                </div>

              <div class="flex justify-end">
                <p class="text-md font-smedium mt-2 text-[#898989]">Fees</p>
              </div>

              <div class="flex justify-between">
                <div class="checkbox flex gap-2 items-center mt-4">
                  <input
                    type="checkbox"
                    value=""
                    class="appearance-none w-4 h-4 bg-[#F1F1F1] checked:bg-[black] rounded p-[10px] cursor-pointer"
                  />
                  <label
                    for="default-checkbox"
                    class="ms-2 text-md font-medium text-gray-900 dark:text-gray-500"
                    >Name-Board</label
                  >
                  <img
                    src="../assets/Info Circle.png"
                    style="width: 14px; height: 13px"
                  />
                </div>
                <p class="text-md font-semibold mt-4 text-black">SAR 0.0</p>
              </div>

              <div class="flex justify-between">
                <div class="checkbox flex gap-2 items-center mt-4">
                  <input
                    id="default-checkbox"
                    type="checkbox"
                    value=""
                    class="appearance-none w-4 h-4 bg-[#F1F1F1] checked:bg-[black] rounded p-[10px] cursor-pointer"
                  />
                  <label
                    for="default-checkbox"
                    class="ms-2 text-md font-medium text-gray-900 dark:text-gray-500"
                    >Child's seat</label
                  >
                </div>
                <p class="text-md font-semibold mt-4 text-black">SAR 130.0</p>
              </div>
              <div class="flex justify-between">
                <div class="checkbox flex gap-2 items-center mt-4">
                  <input
                    id="default-checkbox"
                    type="checkbox"
                    value=""
                    class="appearance-none w-4 h-4 bg-[#F1F1F1] checked:bg-[black] rounded p-[10px] cursor-pointer"
                  />
                  <label
                    for="default-checkbox"
                    class="ms-2 text-md font-medium text-gray-900 dark:text-gray-500"
                    >Altanfithi Accsess</label
                  >
                </div>
                <p class="text-md font-semibold mt-4 text-black">SAR 2,000.0</p>
              </div>
              <div class="flex justify-between">
                <div class="checkbox flex gap-2 items-center mt-4">
                  <input
                    id="default-checkbox"
                    type="checkbox"
                    value=""
                    class="appearance-none w-4 h-4 bg-[#F1F1F1] checked:bg-[black] rounded p-[10px] cursor-pointer"
                  />
                  <label
                    for="default-checkbox"
                    class="ms-2 text-md font-medium text-gray-900 dark:text-gray-500"
                    >Additional car for luggages</label
                  >
                  <img
                    src="../assets/Info Circle.png"
                    style="width: 14px; height: 13px; margin-top: 4px"
                  />
                </div>
                <p class="text-md font-semibold mt-4 text-black">SAR 250.0</p>
              </div>

              <div class="relative">
                <textarea
                  id="message"
                  rows="5"
                  class="block mt-5 pt-6 pl-3 w-full text-sm text-gray-900 bg-gray-100 rounded-lg focus:ring-blue-500 focus:border-blue-500 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500"
                  placeholder="Luggage information, special needs or tasks for driver"
                ></textarea>
                <label
                  class="label left-2 top-0 pt-2 text-sm font-medium text-gray-900 dark:text-white pointer-events-none"
                  >A special comment</label
                >
              </div>
              <div class="flex justify-start mt-4">
                <h1 class="text-md font-bold">Summery</h1>
              </div>
              <div class="flex justify-between">
                <p class="text-sm font-medium mt-2 text-black">Services cost</p>
                <p class="text-sm font-semibold mt-2 text-black">SAR 450.0</p>
              </div>
              <div class="flex justify-between">
                <p class="text-sm font-medium mt-2 text-black">
                  Additions fees
                </p>
                <p class="text-sm font-semibold mt-2 text-black">SAR 2,000.0</p>
              </div>
              <div class="flex justify-between">
                <p class="text-sm font-medium mt-2 text-black">VAT</p>
                <p class="text-sm font-semibold mt-2 text-black">SAR 100.0</p>
              </div>
              <div class="flex justify-between">
                <p class="text-sm font-bold mt-2 text-black">Total</p>
                <p class="text-sm font-bold mt-2 text-black">SAR 2,450.0</p>
              </div>
              <div class="card2 mt-5">
                <div class="flex justify-between">
                  <p class="text-sm font-normal mt-2 text-black">
                    Payment Method
                  </p>
                  <div class="flex gap-2">
                    <p class="text-sm font-bold mt-2 text-black">
                      Balance . SAR 20,450.00
                    </p>
                    <svg
                      @click="openpop"
                      xmlns="http://www.w3.org/2000/svg"
                      viewBox="0 0 320 512"
                      style="width: 11px; margin-top: 6px; cursor: pointer"
                    >
                      <!--!Font Awesome Free 6.5.2 by @fontawesome - https://fontawesome.com License - https://fontawesome.com/license/free Copyright 2024 Fonticons, Inc.-->
                      <path
                        d="M278.6 233.4c12.5 12.5 12.5 32.8 0 45.3l-160 160c-12.5 12.5-32.8 12.5-45.3 0s-12.5-32.8 0-45.3L210.7 256 73.4 118.6c-12.5-12.5-12.5-32.8 0-45.3s32.8-12.5 45.3 0l160 160z"
                      />
                    </svg>
                  </div>
                </div>
                <button
                  type="submit"
                  class="w-full rounded-lg pt-3 py-3 mt-4 text-sm font-semibold bg-[#0000000D] text-gray-400"
                >
                  Submit
                </button>
              </div>
              <div class="relative">
                <div
                  v-if="ispop"
                  class="fixed inset-0 flex items-center justify-center bg-black bg-opacity-[0.1]"
                >
                  <div class="bg-white rounded-lg p-8">
                    <img
                      src="../assets/close.png"
                      class="close"
                      @click="closepop"
                    />
                    <div>
                      <h1 class="text-xl font-bold">Payment Method</h1>
                      <P class="text-sm mb-4"
                        >Please select payment method for your next
                        <br />request</P
                      >
                    </div>
                    <div class="flex gap-2 mb-3">
                      <img src="../assets/empty-wallet.png" />
                      <p class="text-sm font-semibold text-black mt-1">
                        Balance . SAR 20,450.00
                      </p>
                    </div>
                    <hr />
                    <div class="flex gap-2 mb-3">
                      <img src="../assets/Group.png" class="visa" />
                      <p class="text-sm font-semibold mt-2">Visa . 5766</p>
                      <img src="../assets/tick-circle.png" class="tick" />
                    </div>
                    <hr />
                    <div class="flex gap-2 mb-3">
                      <img
                        src="../assets/american-express-logo-black-and-white 1.png"
                        class="circle"
                      />
                      <p class="text-sm font-semibold mt-2">Amex . 5736</p>
                    </div>
                    <hr />
                    <div>
                      <img
                        src="../assets/Child's seat.png"
                        style="width: 53%; margin-top: 11px"
                      />
                    </div>
                  </div>
                </div>
              </div>
            </div>
          </form>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { Swiper, SwiperSlide } from "swiper/vue";
import { Navigation } from "swiper/modules";
import "swiper/css";
import "swiper/css/navigation";
export default {
  data() {
    return {
      isModalOpen: false,
      ispop: false,
    };
  },

  components: {
    Swiper,
    SwiperSlide,
  },

  setup() {
    return {
      modules: [Navigation],
    };
  },

  methods: {
    // Method to open the modal
    openModal() {
      this.isModalOpen = true;
    },

    openpop() {
      this.ispop = true;
    },
    // Method to close the modal
    closeModal() {
      this.isModalOpen = false;
    },

    closepop() {
      this.ispop = false;
    },
  },
};
</script>

<style>
.option-lines {
  white-space: pre-line;
}
.relative {
  position: relative;
}

.label {
  position: absolute;
  top: 0px;
  left: 11px;
}
.card {
  width: 234px;
  height: auto;
}
.card2 {
  box-shadow: 0px -1px 8px 0 rgba(0, 0, 0, 0.2), -1px -2px 9px 0 rgb(0 0 0 / 0%);
  background-color: white;
  border-radius: 10px;
  margin-left: -23px;
  margin-right: -24px;
  padding: 14px;
  margin-bottom: -19px;
}
.image {
  background-image: url("../assets/image.png");
}
.map {
  position: absolute;
  top: -5px;
  right: 12px;
}
.close {
  margin-top: -14px;
  margin-bottom: 12px;
  width: 16px;
  cursor: pointer;
}
.visa {
  width: 26px;
  height: 11px;
  margin-top: 13px;
}
.tick {
  width: 17px;
  height: 17px;
  margin-top: 10px;
  margin-left: auto;
}
.circle {
  width: 13px;
  height: 13px;
  margin-top: 12px;
}
.photo {
  width: 645px;
  height: 335px;
}
.input {
  position: relative;
  top: -386px;
  width: 627px;
  margin-left: 8px;
}
.cont {
  top: -325px;
  position: relative;
  z-index: 1;
  left: 37px;
}
.pin {
  top: -305px;
  position: relative;
  z-index: 1;
  left: 19px;
}
.popup {
  margin-left: 27%;
  margin-top: 9%;
}
.swiper-button-next:after, .swiper-rtl .swiper-button-prev:after {
    content: '';
}
.swiper-button-prev, .swiper-rtl .swiper-button-next {
    left: 195px;
    right: auto;
    bottom: 261px;
}
.swiper-button-next, .swiper-rtl .swiper-button-prev {
    right: -466px;
    left: auto;
    top: -345px;
}
.swiper-button-prev, .swiper-button-next {
    position: relative;
    bottom: 250px;
    /* width: calc(var(--swiper-navigation-size) / 44* 27); */
    /* height: var(--swiper-navigation-size); */
    margin-top: -42px;
    z-index: 10;
    cursor: pointer;
    display: flex;
    align-items: center;
    justify-content: center;
    color: var(--swiper-navigation-color, var(--swiper-theme-color));
}

.swiper-button-prev:after, .swiper-rtl .swiper-button-next:after {
    content: '';
}
</style>
