<template>
  <main class="w-screen h-screen bg-blue-reg">
    <div
      class="w-[410px] py-14 h-[90%] my-auto mx-auto flex flex-col justify-between items-center relative"
    >
      <h1 class="text-silver-reg text-[32px]">pomodoro</h1>
      <ButtonsGroup class="z-10">
        <Button
          @click="changeTime(`pomodoro`)"
          textContent="pomodoro"
          :class="`${pomodoro ? `bg-${mainColor}` : ``}`"
        />
        <Button
          @click="changeTime(`shortBreak`)"
          textContent="short break"
          :class="`${shortBreak ? `bg-${mainColor}` : ``}`"
        />
        <Button
          @click="changeTime(`longBreak`)"
          textContent="long break"
          :class="`${longBreak ? `bg-${mainColor}` : ``}`"
        />
      </ButtonsGroup>
      <mainElement :time="mainTime" />
      <i class="bx bxs-cog text-silver-reg text-2xl" @click="configsToggle"></i>
      <div
        v-if="configs"
        class="configs z-20 absolute top-[140px] rounded-xl h-[544px] w-[580px] bg-white"
      >
        <div class="flex justify-between p-7">
          <h1 class="text-lg-reg text-blue-reg">Settings</h1>
          <i class="bx bx-x text-2xl" @click="configsToggle"></i>
        </div>
        <hr />
        <div class="flex justify-between flex-col mt-6 w-full h-[109px] mb-6">
          <div class="flex justify-between flex-col px-8 h-full">
            <h1 class="text-dark-blue-reg text-body-1-reg">Time (Minutes)</h1>
            <div class="flex justify-between">
              <div class="flex flex-col w-[140px] gap-1">
                <h1
                  class="text-body-2-reg text-xs-reg text-dark-blue-reg opacity-40"
                >
                  pomodoro
                </h1>
                <div
                  class="flex justify-between bg-silver-reg p-[15px] rounded-[10px] h-12"
                >
                  <h1>25</h1>
                  <div class="flex flex-col justify-between">
                    <i class="bx bx-chevron-up w-4 h-3"></i>
                    <i class="bx bx-chevron-down w-4 h-3"></i>
                  </div>
                </div>
              </div>
              <div class="flex flex-col w-[140px] gap-1">
                <h1
                  class="text-body-2-reg text-xs-reg text-dark-blue-reg opacity-40"
                >
                  pomodoro
                </h1>
                <div
                  class="flex justify-between bg-silver-reg p-[15px] rounded-[10px] h-12"
                >
                  <h1>5</h1>
                  <div class="flex flex-col justify-between">
                    <i class="bx bx-chevron-up w-4 h-3"></i>
                    <i class="bx bx-chevron-down w-4 h-3"></i>
                  </div>
                </div>
              </div>
              <div class="flex flex-col w-[140px] gap-1">
                <h1
                  class="text-body-2-reg text-xs-reg text-dark-blue-reg opacity-40"
                >
                  pomodoro
                </h1>
                <div
                  class="flex justify-between bg-silver-reg p-[15px] rounded-[10px] h-12"
                >
                  <h1>15</h1>
                  <div class="flex flex-col justify-center">
                    <i class="bx bx-chevron-up w-4 h-3"></i>
                    <i class="bx bx-chevron-down w-4 h-3"></i>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </div>
        <hr />
        <div class="flex justify-between py-6 px-[40px] items-center">
          <h1>Fonts</h1>
          <div class="flex justify-between w-2/5 items-center">
            <div
              class="rounded-full text-[15px] font-bold text-white p-4 bg-dark-blue-reg"
            >
              Aa
            </div>
            <div
              class="rounded-full text-[15px] font-bold text-[15px] opacity-75 font-RobotoRegular text-blue-reg p-4 bg-silver-reg"
            >
              Aa
            </div>
            <div
              class="rounded-full text-[15px] font-bold font-SpaceRegular text-dark-blue-reg p-4 bg-silver-reg"
            >
              Aa
            </div>
          </div>
        </div>
        <hr />
        <div class="flex justify-between py-6 px-[40px] items-center">
          <h1>Color</h1>
          <div id="themes" class="flex justify-between w-2/5 items-center">
            <div
              @click="changeTheme('red')"
              class="red rounded-full w-[60px] h-[60px] font-bold text-dark-blue-reg p-4 bg-red-reg flex justify-center items-center"
            ></div>
            <div
              @click="changeTheme('blue')"
              class="blue rounded-full w-[60px] h-[60px] font-bold text-dark-blue-reg p-4 bg-[#70F3F8] flex justify-center items-center"
            ></div>
            <div
              @click="changeTheme('pink')"
              class="pink rounded-full w-[60px] h-[60px] font-bold text-dark-blue-reg p-4 bg-[#D881F8] flex justify-center items-center"
            ></div>
          </div>
        </div>
      </div>
    </div>
  </main>
</template>
<script>
import ButtonsGroup from "./components/ButtonsGroup/ButtonsGroup.vue";
import mainElement from "./components/mainElement/mainElement.vue";
import Button from "./ui/Button/Button.vue";
export default {
  name: "App",
  components: {
    ButtonsGroup,
    Button,
    mainElement,
  },

  data() {
    return {
      configs: false,
      pomodoro: true,
      shortBreak: false,
      longBreak: false,
      pomodoroTime: "25:00",
      shortBreakTime: "05:00",
      longBreakTime: "15:00",
      mainTime: this.pomodoroTime,
      redColor: "red-reg",
      blueColor: "[#70F3F8]",
      pinkColor: "[#D881F8]",
      mainColor: this.redColor,
    };
  },
  methods: {
    configsToggle() {
      this.configs = !this.configs;
    },
    changeTime(name) {
      console.log(name, this.mainTime);
      if (name === "pomodoro") {
        if (!this.pomodoro) {
          this.mainTime = this.pomodoroTime;
          this.pomodoro = true;
          this.shortBreak = false;
          this.longBreak = false;
        }
      }
      if (name === "shortBreak") {
        this.mainTime = this.shortBreakTime;
        if (!this.shortBreak) {
          this.shortBreak = true;
          this.pomodoro = false;
          this.longBreak = false;
        }
      }
      if (name === "longBreak") {
        this.mainTime = this.longBreakTime;
        if (!this.longBreak) {
          this.longBreak = true;
          this.pomodoro = false;
          this.shortBreak = false;
        }
      }
    },
    changeTheme(color) {
      if (color == "red") {
        this.mainColor = this.redColor;
      }
      if (color == "blue") {
        this.mainColor = this.blueColor;
      }
      if (color == "pink") {
        this.mainColor = this.pinkColor;
      }
    },
  },
  mounted() {
    this.mainTime = this.pomodoroTime;
    this.mainColor = this.redColor;
  },
};
</script>
<style></style>
