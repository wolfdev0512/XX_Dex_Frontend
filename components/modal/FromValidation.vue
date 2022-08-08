<template>
  <div class="w-full py-[15px] h-full border-1 text-white max-w-[500px]">
    <div
      class="text-white text-center m-[10px] font-medium text-[25px] border-1"
    >
      FORM_VALIDATION
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

      <div class="px-[30px] pt-[30px]">
        <div class="flex mb-[20px]">
          <div class="w-1/2">
            <div>{{ flag ? "I buy" : "I sell" }}</div>
            <div class="flex gap-[15px] my-[5px] items-center">
              <input class="w-[100px] leading-[40px] bg-transparent border-2" />
              <div>xx</div>
            </div>
          </div>
          <div class="w-1/2 pl-[20px]">
            <div>{{ flag ? "I pay a maximum of" : "At the price of" }}</div>
            <div class="flex gap-[15px] my-[5px] items-center">
              <input class="w-[70px] leading-[40px] bg-transparent border-2" />
              <div>USDT per xx</div>
            </div>
          </div>
        </div>
        <div v-if="flag" class="flex flex-col gap-[10px]">
          <div class="flex items-center gap-[10px]">
            <img :src="coinImage2" class="w-[30px]" />
            <div>USDT Refund Address*</div>
          </div>
          <input class="leading-[30px] bg-transparent border-2" />
          <br />

          <div class="flex items-center gap-[10px]">
            <img :src="coinImage1" class="w-[30px]" />
            <div>XX Receive Address</div>
          </div>
          <input class="leading-[30px] bg-transparent border-2" />
        </div>
        <div v-else class="flex flex-col gap-[10px]">
          <div class="flex items-center gap-[10px]">
            <img :src="coinImage1" class="w-[30px]" />
            <div>XX Receive Address</div>
          </div>
          <input class="leading-[30px] bg-transparent border-2" />
          <br />
          <div class="flex items-center gap-[10px]">
            <img :src="coinImage2" class="w-[30px]" />
            <div>USDT Refund Address*</div>
          </div>
          <input class="leading-[30px] bg-transparent border-2" />
        </div>

        <br />
        <div class="flex gap-[10px]">
          <Checkbox id="binary" v-model="check" :binary="true" />
          <div>
            I agree that if my order is not matched within 2 hours, I will be
            refunded at this address. This is a fill-or-kill order, to be
            executed in its entirety, otherwise cancelled. There are no partial
            execution, we will refund the full amount minus network fees
          </div>
        </div>
        <br />
        <div class="flex flex-col">
          <div
            class="flex justify-center text-[25px] font-bold gap-[20px] mb-[10px]"
          >
            <div class="text-right">Estimated cost:</div>
            <div class="">{{ flag ? "24 USDT" : "1484 USDT" }}</div>
          </div>
          <div class="flex gap-[20px]">
            <div class="w-1/2 text-right">
              {{ flag ? "24 USDT" : "1500 USDT" }}
            </div>
            <div class="w-1/2">
              {{ flag ? "20 XX @ 2 USDT" : "500 XX @ 3 USDT" }}
            </div>
          </div>
          <div class="flex gap-[20px]">
            <div class="w-1/2 text-right">
              {{ flag ? "2 USDT" : "-1 USDT" }}
            </div>
            <div class="w-1/2">network fee</div>
          </div>
          <div class="flex gap-[20px]">
            <div class="w-1/2 text-right">
              {{ flag ? "2 USDT" : "-15 USDT" }}
            </div>
            <div class="w-1/2">servive fee</div>
          </div>
        </div>
        <br />
        <div class="flex justify-center">
          <Button
            class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-1 px-4 rounded"
          >
            START ORDER
          </Button>
        </div>
      </div>
    </div>
  </div>
</template>
<script lang="ts">
import { defineComponent, ref } from "vue";
import Checkbox from "primevue/checkbox";

// assets
import coinImage1 from "~/assets/image/xx.png";
import coinImage2 from "~/assets/image/usdt.png";
export default defineComponent({
  components: { Checkbox },
  setup() {
    const flag = ref(true);
    const str = ref("string");
    const check = ref(false);
    return {
      coinImage1,
      coinImage2,
      flag,
      str,
      check,
    };
  },
});
</script>
