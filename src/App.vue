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
  font-size: 16px;
  font-family: 'Noto Sans JP', sans-serif;
  color: white;
  background-color: #292929;
}

a,a:visited,a:active{
  color: white;
  text-decoration: none;
}
</style>
