<template>
  <div id="app">
    <h1>マイナンバーカードを健康保険証として利用できる医療機関検索ツール</h1>
    <p>(最終更新日: 2021/10/20)</p>
    <p><a href="https://www.mhlw.go.jp/stf/index_16743.html">こちら</a>の厚労省のページから CSV をダウンロードしてきて検索しやすいようにしたものです。<br>情報が最新でない場合がありますがご容赦ください。<br>このページのソースコードは<a href="https://github.com/pn11/maah">こちら</a>です。</p>
    <HelloWorld />
  </div>
</template>

<script>
import HelloWorld from "./components/HelloWorld.vue";

export default {
  name: "App",
  components: {
    HelloWorld,
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
