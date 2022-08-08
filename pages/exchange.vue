<template>
  <div class="w-screen bg-black min-h-screen py-[30px] px-[20px]">
    <div
      class="relative w-full grid grid-cols-1 lg:grid-cols-2 2xl:grid-cols-3 desktop:grid-cols-4 border-1"
    >
      <div class="absolute top-0 left-0">
        <img :src="logoImage" class="w-[50px] border-1" />
      </div>
      <div class="flex justify-center">
        <ModalFromValidation />
      </div>
      <div class="flex justify-center">
        <ModalWaitForDeposit />
      </div>
      <div class="flex justify-center">
        <ModalWaitingForConfirmation />
      </div>
      <div class="flex justify-center">
        <ModalOrderCreated />
      </div>
    </div>
  </div>
</template>

<script lang="ts">
import { defineComponent, ref } from "vue";
import SelectButton from "primevue/button";
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
  components: {
    SelectButton,
  },
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
