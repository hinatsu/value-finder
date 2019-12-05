<template>
  <div id="app">
    <div id="nav">
      <div id="title">Value Finder</div>
      <div>
        <div>1.あなたの価値観に沿って単語を全て振り分けてみましょう。</div>
        <div>2.最も重要な価値観を10個に絞ってみましょう。</div>
        <div>3.絞った価値観に順位をつけてみましょう</div>
      </div>
    </div>
    <router-view />
  </div>
</template>

<style lang="scss">
html {
  background-color: #ffeee2;
  #title {
    font-size: 2.5rem;
  }
}
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

#nav {
  padding: 30px;

  a {
    font-weight: bold;
    color: #2c3e50;

    &.router-link-exact-active {
      color: #42b983;
    }
  }
}
</style>
