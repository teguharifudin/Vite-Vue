<script setup>
defineProps({
  type: {
    type: String,
    default: "submit",
  },
});
</script>

<template>
  <button :type="type" class="items-center border border-transparent rounded-md text-xs tracking-wides ease-in-out duration-150 !text-[#fff] bg-[#008aff] bg-[-webkit-linear-gradient(135deg,_#6B02FF_0%,_#985BEF_100%)] bg-[-o-linear-gradient(bottom_right,_#6B02FF,_#985BEF)] bg-[-moz-linear-gradient(bottom_right,_#008aff,_#1ad2fd)] bg-[linear-gradient(135deg,_#6B02FF_0%,_#985BEF_100%)] [transition:all_0.5s_ease] font-['Roboto',_sans-serif] text-[16px] leading-[22px] font-medium rounded-tl-[6px] rounded-br-[6px] rounded-tr-[6px] rounded-bl-[6px] mx-[0] my-[10px] px-[30px] py-[16px] inline-block [transition:all_0.4s_ease-in-out]">
    <slot />
  </button>
</template>