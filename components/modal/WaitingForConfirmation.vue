<template>
  <div class="w-full py-[15px] h-full border-1 max-w-[500px]">
    <div
      class="text-white text-center m-[10px] font-medium text-[25px] border-1"
    >
      WAITING_FOR_CONFIRMATION
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
        Deposit detected<br />
        {{
          flag
            ? coin1Amount.amount + " " + coin1Amount.type
            : coin2Amount.amount + " " + coin2Amount.type
        }}
      </div>
      <div class="text-center my-[20px]">
        <i class="pi pi-check order-check"></i>
      </div>
      <div class="text-white text-center text-[20px] font-bold mt-[10px]">
        Waiting for X confirmations<br />before creating the order
      </div>
      <br />
      <div class="text-white text-center text-[20px] font-normal">
        When your order is matched<br />
        you will receive:
        {{
          flag
            ? coin3Amount.amount + " " + coin3Amount.type
            : coin4Amount.amount + " " + coin4Amount.type
        }}
        <br />
        <br />
        Unmatched order within 24 hours are refunded
      </div>
      <br />
      <div class="flex justify-center">
        <Button
          class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-1 px-4 rounded"
        >
          CLOSE
        </Button>
      </div>
    </div>
  </div>
</template>
<script lang="ts">
import { defineComponent, ref } from "vue";
import Button from "primevue/button";

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
    };
  },
});
</script>

<style>
.order-check {
  font-size: 50px;
  font-weight: 900;
  color: rgb(81, 255, 0);
}
</style>
