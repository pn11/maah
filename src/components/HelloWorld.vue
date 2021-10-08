<template>
  <div class="hello">
    <p>毎回情報を入力するのが面倒なので楽するためのやつです。全て半角で入力してください。</p>
    <p>市区町村コード: <input v-model="cityCode" placeholder="市区町村コード"></p>
    <p>接種券番号: <input v-model="couponNum" placeholder="接種券番号"></p>
    <p>生年月日: <input type="number" min="1901" max="2021" v-model="year" placeholder="年(西暦)">年<input type="number" min="1" max="12" v-model="month" placeholder="月">月<input min="1" max="31" type="number" v-model="day" placeholder="日">日</p>
    <p><button type="button" @click="doCopy">クリップボードにコピー</button> または <a v-bind:href=bookmarklet>ブックマークバーにドラッグ</a></p>
    <code>{{ bookmarklet }}</code>
    <h3>使用方法</h3>
    <ul>
      <li>上のテキストボックスに必要事項を入力するとブックマークレットが生成されるので、ブラウザに登録して利用してください。</li>
      <li>登録方法は <a href=https://qiita.com/aqril_1132/items/b5f9040ccb8cbc705d04>ブックマークレットの登録方法 - Qiita</a> などを参照してください。</li>
      <li>本ページで入力された情報はブラウザ内でのみ使用されます。このページのソースコードは<a href="https://github.com/pn11/vaccine-sdftokyo">こちら</a>です。</li>
    </ul>
    <img alt="demo" src="../assets/demo.gif">
  </div>
</template>

<script>
import { copyText } from "vue3-clipboard";

export default {
  name: "HelloWorld",
  components: {},
  data() {
    return {
      cityCode: "",
      couponNum: "",
      year: 1901,
      month: 1,
      day: 1,
    };
  },
  computed: {
    bookmarklet: function () {
      return (
        'javascript:(function(){cityCode="' +
        this.cityCode +
        '";couponNum="' +
        this.couponNum +
        '";year=' +
        this.year +
        ";month=" +
        this.month +
        ";day=" +
        this.day +
        ';document.querySelector("#VisitnoAuthName").value=cityCode;document.querySelector("#VisitnoAuthVisitno").value=couponNum;document.querySelector("#VisitnoAuthYear").selectedIndex=year-1901;document.querySelector("#VisitnoAuthMonthMonth").selectedIndex=month-1;document.querySelector("#VisitnoAuthDayDay").selectedIndex=day-1;})()'
      );
    },
  },
  methods: {
    doCopy: function () {
      copyText(this.bookmarklet, undefined, (error, event) => {
        if (error) {
          // alert("Can not copy");
          console.log(error);
        } else {
          // alert("Copied");
          console.log(event);
        }
      });
    },
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
