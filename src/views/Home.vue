<template>
  <div class="container">
    <div class="main">
      <div class="cover">
        <img src="@/assets/cover.png" alt="" />
      </div>
      <div class="text">
        <p><a href="#" class="join">Join</a><br />the release party of the</p>
        <h2><span class="nowrap">Software Architecture with C++</span></h2>
      </div>
    </div>
    <div class="counter">00:00:00</div>
  </div>
</template>

<script>
export default {
  name: "Home",
};
</script>
<style lang="scss" scoped>
$colors: (
  "first": #ffb43b,
  "second": #f5711c,
  "black": #141414,
);

.container {
  margin: auto;
  width: 70%;
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
    box-shadow: 15px 20px 35px #005;
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

  .nowrap {
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

@keyframes underline-gradient {
  0% {
    transform: translate3d(0%, 0%, 0);
  }
  100% {
    transform: translate3d(-75%, 0%, 0);
  }
}
</style>
