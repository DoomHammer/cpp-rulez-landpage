<template>
  <div class="clock" :title="targetDate">
    <div class="numbers">
      <div class="box">
        <div class="header">Days</div>
        <div class="nums">
          <Replacer :content="singleChar('days', 0)" />
          <Replacer :content="singleChar('days', 1)" />
        </div>
      </div>
      <div class="box">
        <div class="header">Hours</div>
        <div class="nums">
          <Replacer :content="singleChar('hours', 0)" />
          <Replacer :content="singleChar('hours', 1)" />
        </div>
      </div>
      <div class="box">
        <div class="header">Minutes</div>
        <div class="nums">
          <Replacer :content="singleChar('minutes', 0)" />
          <Replacer :content="singleChar('minutes', 1)" />
        </div>
      </div>
      <div class="box">
        <div class="header">Seconds</div>
        <div class="nums">
          <Replacer :content="singleChar('seconds', 0)" />
          <Replacer :content="singleChar('seconds', 1)" />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Replacer from "@/components/Replacer";
import moment from "moment";

export default {
  name: "Clock",
  components: {
    Replacer,
  },
  data() {
    const targetDate = moment("2021-04-09 15:00 +0000", "YYYY-MM-DD HH:mm Z"); // parsed as UTC
    const now = moment();
    const freeze = now.isAfter(targetDate);

    return {
      days: targetDate.diff(now, "days"),
      hours: targetDate.diff(now, "hours") % 24,
      minutes: targetDate.diff(now, "minutes") % 60,
      seconds: targetDate.diff(now, "seconds") % 60,
      targetDate: targetDate.format(),
      handler: "",
      freeze
    };
  },
  created() {
    this.handler = setInterval(this.update.bind(this), 1000);
  },
  destroyed() {
    clearInterval(this.handler);
  },
  methods: {
    update() {
      --this.seconds;

      if (this.seconds < 0) {
        if (this.minutes <= 0 && this.hours <= 0){
          this.freeze = true;
          return;
        }

        this.seconds = 59;
        --this.minutes;
      }

      if (this.minutes < 0) {
        this.minutes = 59;
        --this.hours;
      }

      if (this.hours < 0) {
        this.hours = 23;
        --this.days;
      }
    },
    singleChar(prop, i) {
      if (this.freeze) return "0";
      
      const vs = this[prop].toString();

      if (vs.length < 2) {
        if (i == 0) return "0";
        return vs[0];
      }

      return vs[i];
    },
  },
};
</script>

<style lang="scss">
.numbers {
  text-align: center;
  font-size: 1.7em;
}
.box {
  display: inline-block;
  margin: 0.2em;
  width: 5em;

  .header {
    color: #fff;
    font-size: 0.6em;
    background-color: #3d3d3d;
    border-bottom: 2px solid #f5711c;
    margin: 0;
  }

  .nums {
    background-color: #3d3d3d;
    color: white;
    padding: 1em;
  }
  box-shadow: 1px 1px 15px 1px darken(#f5711c, 50%);
}

@media only screen and (max-width: 500px) {
  .numbers .box {
    width: 40%;
  }
}
</style>
