<template>
  <div class="w-full py-[15px] h-full border-1 max-w-[500px]">
    <div
      class="text-white text-center m-[10px] font-medium text-[25px] border-1"
    >
      WAITING_FOR_DEPOSIT
    </div>
    <div class="border-1 rounded-[5px] py-[20px]">
      <div v-if="flag" class="flex flex-row">
        <div
          class="flex-1 rounded-[5px] p-[10px] border-3 font-bold text-white text-center text-[20px]"
        >
          BUY XX
        </div>
        <div
          class="flex-1 rounded-[5px] p-[10px] border-1 text-white text-center text-[20px]"
          v-on:click="flag = false"
        >
          SELL XX
        </div>
      </div>
      <div
        v-else
        v-on:click="flag = true"
        class="flex flex-row text-white text-center text-[20px]"
      >
        <div
          class="flex-1 rounded-[5px] p-[10px] border-1"
          v-on:click="flag = false"
        >
          BUY XX
        </div>
        <div
          class="flex-1 rounded-[5px] p-[10px] border-3 font-bold text-white text-center text-[20px]"
        >
          SELL XX
        </div>
      </div>
      <div class="text-white text-center text-[20px] font-bold mt-[20px]">
        Waiting for you to send exactly;<br />
        {{
          flag
            ? coin1Amount.amount + " " + coin1Amount.type
            : coin2Amount.amount + " " + coin2Amount.type
        }}
      </div>
      <div v-if="flag" class="text-white text-[15px] text-center">
        The deposit address is only valid for 14:37

        <div class="flex justify-center items-center gap-[10px]">
          <img :src="coinImage2" class="w-[30px]" />
          <div>
            <span class="text-[20px] font-bold text-green-500">0x777</span>
            <span>TemporaryColdStorageAddress</span>
            <span class="text-[20px] font-bold text-green-500">42bt4</span>
          </div>
        </div>
      </div>
      <div
        v-else
        class="text-white text-[15px] text-center flex justify-center items-center gap-[10px]"
      >
        <div>:to</div>
        <img :src="coinImage1" class="w-[30px]" />
        <div>
          <span class="text-[20px] font-bold text-blue-600">6Temp</span>
          <span>1RQTeage2P3XR3z</span>
          <span class="text-[20px] font-bold text-blue-600">5Stor</span>
        </div>
      </div>
      <div class="flex flex-col items-center m-[20px]">
        <img :src="flag ? qrImage2 : qrImage1" class="w-[200px]" />
        <div class="text-[15px] text-white">Request:1234</div>
      </div>
      <br />
      <div v-if="flag" class="text-white text-center text-[15px] font-normal">
        You will receive
        <span class="font-bold">
          {{ coin3Amount.amount + " " + coin3Amount.type }}
        </span>
        at:
        <br />
        <div
          class="text-white text-[12px] text-center flex justify-center items-center gap-[10px]"
        >
          <img :src="coinImage1" class="w-[25px]" />
          <div>
            <span class="text-[15px] font-bold text-blue-600">6ZBak</span>
            <span>1RQBnCBAa2WFRSDnsYc2DjoQTyMQU2BpP3XR3z</span>
            <span class="text-[15px] font-bold text-blue-600">7BBZC</span>
          </div>
        </div>
        <br />
        Your USDT Refund Address
        <div
          class="text-white text-[12px] text-center flex justify-center items-center gap-[10px]"
        >
          <img :src="coinImage2" class="w-[30px]" />
          <div>
            <span class="text-[15px] font-bold text-green-500">0x1f7</span>
            <span>7448b1ff9b118772f79e8862886284163bef</span>
            <span class="text-[15px] font-bold text-green-500">47fd3</span>
          </div>
        </div>
      </div>
      <div v-else class="text-white text-center text-[15px] font-normal">
        You will receive
        {{ coin4Amount.amount + " " + coin4Amount.type }}
        at:
        <br />
        <div
          class="text-white text-[12px] text-center flex justify-center items-center gap-[10px]"
        >
          <img :src="coinImage2" class="w-[30px]" />
          <div>
            <span class="text-[15px] font-bold text-green-500">0x1f7</span>
            <span>7448b1ff9b118772f79e8862886284163bef</span>
            <span class="text-[15px] font-bold text-green-500">47fd3</span>
          </div>
        </div>
        <br />
        Your XX Refund Address
        <div
          class="text-white text-[12px] text-center flex justify-center items-center gap-[10px]"
        >
          <img :src="coinImage1" class="w-[25px]" />
          <div>
            <span class="text-[15px] font-bold text-blue-600">6ZBak</span>
            <span>1RQBnCBAa2WFRSoQU2BpP3XR3z</span>
            <span class="text-[15px] font-bold text-blue-600">7BBZC</span>
          </div>
        </div>
      </div>
      <br />
      <div class="flex justify-center">
        <Button
          class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-1 px-4 rounded"
        >
          CANCEL
        </Button>
      </div>
    </div>
  </div>
</template>
<script lang="ts">
import { defineComponent, ref } from "vue";
import Button from "primevue/button";
import coinImage1 from "~/assets/image/xx.png";
import coinImage2 from "~/assets/image/usdt.png";
import qrImage1 from "~/assets/image/QR_xx.png";
import qrImage2 from "~/assets/image/QR_usdt.png";

export default defineComponent({
  components: { Button },
  setup() {
    let flag = ref(true);
    let coin1Amount = ref({
      amount: 24.0,
      type: "USDT",
    });
    let coin2Amount = ref({
      amount: 500,
      type: "XX",
    });

    let coin3Amount = ref({
      amount: 10,
      type: "XX",
    });
    let coin4Amount = ref({
      amount: 1484,
      type: "USDT",
    });

    return {
      flag,
      coin1Amount,
      coin2Amount,
      coin3Amount,
      coin4Amount,
      coinImage1,
      coinImage2,
      qrImage1,
      qrImage2,
    };
  },
});
</script>
