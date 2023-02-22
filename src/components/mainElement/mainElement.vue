<template>
  <div
    class="circle w-[410px] h-[410px] rounded-full flex justify-center items-center"
  >
    <div
      class="rounded-full bg-dark-blue-reg w-[366px] h-[366px] flex justify-center items-center"
    >
      <div
        class="w-[339px] h-[339px] bg-red-reg rounded-full flex justify-center items-center"
      >
        <div
          class="text-silver-reg w-[304px] h-[310px] rounded-full bg-dark-blue-reg"
        >
          <div class="m-[32%] flex jusfity-between flex-col items-center">
            <h1 class="text-xl-reg">{{ time }}</h1>
            <p class="text-base-reg uppercase">pause</p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  name: "mainElement",
  props: {
    time: String,
  },
};
</script>
<style>
.circle {
  background: linear-gradient(315deg, #2e325a 0%, #0e112a 100%);
  box-shadow: -50px -50px 100px #272c5a, 50px 50px 100px #121530;
}
</style>
