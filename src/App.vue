<template>
  <div id="app">
    <router-view/>
  </div>
</template>

<style lang="scss">
@import url('https://fonts.googleapis.com/css2?family=Noto+Sans+JP:wght@100;400;700&display=swap');

*,body,html{
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body{
  background: rgb(63,94,251);
  background: radial-gradient(circle, rgba(63,94,251,1) 0%, rgba(70,169,252,1) 100%);
  font-size: 16px;
  font-family: 'Noto Sans JP', sans-serif;
  color: white;
}

a,a:visited,a:active{
  color: white;
  text-decoration: none;
}
</style>
