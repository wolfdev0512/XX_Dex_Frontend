<template>
  <div
    class="flex flex-col w-screen bg-black min-h-screen py-[40px] sm:px-[30px] gap-[30px]"
  >
    <div class="flex flex-col lg:flex-row w-full border-1 lg:gap-[30px]">
      <div
        class="py-[30px] text-white font-bold text-center lg:hidden text-4xl sm:text-6xl border-1"
      >
        XX Coins Trade Club
      </div>

      <div class="flex-1 flex-col items-center border-1">
        <div
          class="flex justify-center items-end border-1 gap-x-[10px] sm:gap-x-[20px] pt-5 pb-2.5"
        >
          <div class="flex flex-col border-1">
            <p
              class="w-[90px] sm:w-[130px] text-white text-center text-4xl sm:text-6xl font-bold"
            >
              {{ coin1.text }}
            </p>
            <div class="flex justify-center">
              <img
                class="w-[30px] sm:w-[40px]"
                :src="coin1.image"
                alt="No Coin1"
              />
            </div>
          </div>
          <div class="border-1">
            <img
              class="w-[100px] sm:w-[120px]"
              :src="logoImage"
              alt="No Coin1"
            />
          </div>
          <div class="flex flex-col border-1">
            <p
              class="w-[90px] sm:w-[130px] text-white text-center text-4xl sm:text-6xl font-bold"
            >
              {{ coin2.text }}
            </p>
            <div class="flex justify-center">
              <img
                class="w-[30px] sm:w-[40px]"
                :src="coin2.image"
                alt="No Coin1"
              />
            </div>
          </div>
        </div>
        <div class="flex justify-center mt-[50px]">
          <Button
            class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded"
          >
            TRADE NOW
          </Button>
        </div>
        <p class="text-white text-center text-[20px] sm:text-[30px] mt-[25px]">
          Privacy is a right, not a privilege
        </p>
      </div>
      <div class="flex-1 flex-col border-1">
        <div
          class="hidden lg:block p-[15px] pb-[70px] text-white font-bold text-6xl border-1"
        >
          XX Coins<br />
          Trade Club
        </div>
        <div
          class="mt-[20px] p-[15px] pt-[20px] text-white font-semibold text-[20px] sm:text-[26px] xl:text-[36px] border-1 text-center"
        >
          Transparent order book matching.<br />
          all traders are public.
        </div>
        <div
          class="mt-[20px] p-[10px] pr-[20px] text-white font-normal text-[17px] sm:text-[22px] xl:text-[30px] border-1 text-right"
        >
          NO SIGN-UP<br />
          NO ACCOUNT REQUIRED<br />
          1% Service Fees + Actual Network Fees
        </div>
      </div>
    </div>
    <div
      class="flex flex-col lg:flex-row justify-center lg:justify-between border-1 gap-[30px] lg:gap-[50px] xl:gap-[100px] box-border"
    >
      <div
        v-for="(item, index) in WorkStepList"
        v-bind:key="index"
        class="w-full"
      >
        <WorkStep :data="item" :itemIndex="index" />
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from "vue";
import Button from "primevue/button";
// assets
import coinImage1 from "~/assets/image/xx.png";
import coinImage2 from "~/assets/image/usdt.png";
import logoImage from "~/assets/image/logo.png";
//type
import { WorkStepProps } from "~/types/workstep";

const WorkStepList: WorkStepProps[] = [
  {
    flag: false,
    text: "Choose Buy or Sell",
    detail: ["Price", "Amount"],
  },
  {
    flag: false,
    text: "Deposit Funds",
    detail: ["Secure temporary wallet", "No custodial services"],
  },
  {
    flag: true,
    text: "Watch your Order",
    detail: [
      "Wait for order to fullfill",
      "Refundable if order fails to fullfill within 24 hours",
    ],
  },
];

interface CoinType {
  text: string;
  image: any;
}

export default defineComponent({
  components: { Button },
  setup() {
    const coin1 = ref<CoinType>({
      text: "XX",
      image: coinImage1,
    });
    const coin2 = ref<CoinType>({
      text: "USDT",
      image: coinImage2,
    });

    return {
      coin1,
      coin2,
      logoImage,
      WorkStepList,
    };
  },
});
</script>
