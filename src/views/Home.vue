<template>
  <div class="container">
    <div class="main">
      <div class="cover">
        <img src="@/assets/cover.png" alt="" />
      </div>
      <div class="text">
        <p class="smaller">
          <a href="#add-to-calendar" class="join bigger">Join</a><br />the release party of
        </p>
        <h2 class="nowrap">Software Architecture with C++</h2>
        <p class="smaller">
          by <span class="nowrap-s bigger">Adrian Ostrowski</span> and
          <span class="nowrap-s bigger">Piotr Gaczkowski</span>
        </p>
      </div>
    </div>
    <div class="countdown">
      <h3>Coming soon!</h3>
      <Clock />
      <p class="date">9th April 2021 <span class="mainc">16:00</span>-18:00 GMT</p>
      <p class="date" id="add-to-calendar">
    <a href="https://calendar.google.com/calendar/render?action=TEMPLATE&dates=20210409T150000Z%2F20210409T170000Z&details=Come%20join%20our%20party%21%20You%27re%20invited.%0A%0AThe%20meeting%20link%20will%20appear%20at%20https%3A%2F%2Freleaseparty.netlify.app%20an%20hour%20before%20the%20party.&location=https%3A%2F%2Freleaseparty.netlify.app&text=Release%20Party%20%7C%20Software%20Architecture%20with%20C%2B%2B" class="addToCalendar">Add to Calendar (Google)</a>
    <a href="https://outlook.live.com/calendar/0/deeplink/compose?body=Come%20join%20our%20party%21%20You%27re%20invited.%0A%0AThe%20meeting%20link%20will%20appear%20at%20https%3A%2F%2Freleaseparty.netlify.app%20an%20hour%20before%20the%20party.&enddt=2021-04-09T17%3A00%3A00%2B00%3A00&location=https%3A%2F%2Freleaseparty.netlify.app&path=%2Fcalendar%2Faction%2Fcompose&rru=addevent&startdt=2021-04-09T15%3A00%3A00%2B00%3A00&subject=Release%20Party%20%7C%20Software%20Architecture%20with%20C%2B%2B" class="addToCalendar">Add to Calendar (Outlook)</a>
    <a href="https://outlook.office.com/calendar/0/deeplink/compose?body=Come%20join%20our%20party%21%20You%27re%20invited.%0A%0AThe%20meeting%20link%20will%20appear%20at%20https%3A%2F%2Freleaseparty.netlify.app%20an%20hour%20before%20the%20party.&enddt=2021-04-09T17%3A00%3A00%2B00%3A00&location=https%3A%2F%2Freleaseparty.netlify.app&path=%2Fcalendar%2Faction%2Fcompose&rru=addevent&startdt=2021-04-09T15%3A00%3A00%2B00%3A00&subject=Release%20Party%20%7C%20Software%20Architecture%20with%20C%2B%2B" class="addToCalendar">Add to Calendar (Office 365)</a>
    <a href="/releaseparty.ics" class="addToCalendar">Add to Calendar (iCalendar and others)</a>
    </p>
    </div>
  </div>
</template>

<script>
import Clock from "@/components/Clock.vue";

export default {
  name: "Home",
  components: { Clock },
};
</script>
<style lang="scss" scoped>
$colors: (
  "first": #ffb43b,
  "second": #f5711c,
  "black": #141414,
);

.addToCalendar {background-color:#44c767;border-radius:28px;border:1px solid #18ab29;display:inline-block;cursor:pointer;color:#ffffff;font-family:Arial;font-size:14px;padding:16px 31px;text-decoration:none;text-shadow:0px 1px 0px #2f6627;}.addToCalendar:hover {background-color:#5cbf2a;}.addToCalendar:active {position:relative;top:1px;}

.container {
  margin: auto;
  width: 70%;
}

.smaller {
  font-size: 0.7em;
}

.bigger {
  font-size: 1.4em;
}

.mainc {
  color: #f5711c;
}

.main {
  display: flex;
  flex-direction: row;
  justify-content: space-around;
  width: 100%;
  margin-top: 3em;
  padding: 2em;
}

.cover {
  max-width: 30%;
  perspective: 900px;
  margin-right: 2em;

  img {
    max-width: 100%;
    transform: scale3d(1, 1, 1) rotateY(-10deg);
    box-shadow: 15px 20px 35px #224;
  }
}

.text {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  padding: 1.7em;
  font-size: 2em;
  background-color: #3d3d3d;
  text-align: center;
  z-index: 1;

  h2 {
    color: #f5711c;
    font-size: 1.2em;

    small {
      color: white;
    }
  }

  .nowrap, .nowrap-s {
    white-space: nowrap;
  }
}

.join {
  display: inline-block;
  overflow: hidden;
  position: relative;
  vertical-align: bottom;
  transition: all 0.5s;
  font-weight: bold;
  padding: 0.5em 1em;
  animation: btnWiggle 5s infinite;

  &:after {
    background: rgba(0, 0, 0, 0) center 1.98em / 100% 8px no-repeat;
    background-image: linear-gradient(
      45deg,
      rgba(map_get($colors, "second"), 1) 15%,
      rgba(map_get($colors, "first"), 1) 35%,
      rgba(map_get($colors, "second"), 1) 85%
    );

    animation: underline-gradient 6s linear alternate infinite;
    transition: all 0.5s;

    content: "";
    height: 100%;
    left: 0;
    position: absolute;
    top: 5px;
    width: 400%;
    will-change: transform;
    z-index: -1;
  }

  &:hover {
    color: #3d3d3d;
    &:after {
      background-size: 100% 100%;
      background-position-y: center;
    }
  }
}

.countdown {
  h3 {
    text-align: center;
    padding: 1em;
    margin: 0 2rem;
    letter-spacing: 0.1em;
    font-size: 1.7em;
  }

  .date {
    text-align: center;
    margin-top: 1em;
    font-size: 1.4em;
  }
}

@keyframes underline-gradient {
  0% {
    transform: translate3d(0%, 0%, 0);
  }
  100% {
    transform: translate3d(-75%, 0%, 0);
  }
}
@keyframes btnWiggle {
  0% {
    -webkit-transform: rotate(0deg) scale(1);
  }
  2% {
    -webkit-transform: rotate(-2deg) scale(1.1);
  }
  3.5% {
    -webkit-transform: rotate(2deg) scale(0.9);
  }
  5% {
    -webkit-transform: rotate(0deg) scale(1);
  }
  100% {
    -webkit-transform: rotate(0deg) scale(1);
  }
}

@media only screen and (max-width: 1600px) {
  .container {
    width: 85%;
  }
}

@media only screen and (max-width: 1250px) {
  .container {
    width: 100%;
  }
}

@media only screen and (max-width: 1050px) {
  .main {
    flex-direction: column;
    align-items: center;
  }

  .cover {
    max-width: 60%;
    margin-bottom: 4em;
    margin-right: 0;
    perspective: initial;

    img {
      box-shadow: 0 0 65px #224;
    }
  }

  .countdown {
    margin-bottom: 5em;
  }
}

@media only screen and (max-width: 550px) {
  .main {
    padding: 0;
  }
  
  .cover {
    max-width: 80%;
  }
  .text .nowrap {
    white-space: initial;
  }
}
</style>
