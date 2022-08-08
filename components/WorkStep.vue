<template>
  <div class="w-full border-1 px-[30px] py-[15px] h-full">
    <div class="flex items-end gap-[40px]">
      <div
        class="text-cyan-400 text-[70px] xl:text-[100px] font-bold leading-none"
      >
        {{ itemIndex }}
      </div>
      <div v-if="data.flag">
        <i class="pi pi-check check"></i>
      </div>
      <div v-else>
        <i class="pi pi-arrow-right arrows"></i>
      </div>
    </div>
    <div
      class="text-white font-semibold text-[30px] lg:text-[25px] xl:text-[30px]"
    >
      {{ data.text }}
    </div>
    <li
      v-for="(detailItem, index) in data.detail"
      v-bind:key="index"
      class="text-white text-[20px] lg:text-[16px] xl:text-[20px] leading-6"
    >
      {{ detailItem }}
    </li>
  </div>
</template>
<script lang="ts">
import { PropType, defineComponent } from "vue";
import { WorkStepProps } from "~/types/workstep";

export default defineComponent({
  props: {
    data: {
      required: true,
      type: Object as PropType<WorkStepProps>,
    },
    itemIndex: {
      require: true,
      type: Number,
    },
  },
});
</script>

<style>
.check {
  font-size: 70px;
  font-weight: 900;
  color: rgb(34, 211, 238);
}
.arrows {
  font-size: 70px;
  font-weight: 900;
  color: rgba(34, 211, 238, 0.5);
}
</style>
