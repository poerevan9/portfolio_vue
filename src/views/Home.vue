<template>
  <div class="home" v-if="!turnOff">
    <img alt="Vue logo" src="../assets/logo.png" />
    <!-- <HelloWorld msg="Welcome to Your Vue.js App" /> -->
    <header>header</header>

    <!-- Vue life cycle -->
    {{ loading }}
    <a-skeleton :loading="loading">
      <main id="main-area">
        <p>#id, .class</p>
        <h1>h1</h1>
        <article>
          <h1>h1 in article</h1>
          <section>
            <h1>h1 in section</h1>
            <h2>h2</h2>
            <h3>h3</h3>
            <h4>h4</h4>
            <h5>h5</h5>
            <h6>h6</h6>
            <p>
              paragraph <b>bold</b> <strong>strong</strong> <i>italic</i>
              <strike>strike</strike>
            </p>
            <blockquote>blockquote</blockquote>
            <marquee behavior="" direction="">消失在時間的洪流裡了</marquee>
          </section>
        </article>
        <table>
          <caption>
            table
          </caption>
          <thead>
            <tr>
              <th colspan="2">The table header</th>
            </tr>
          </thead>
          <tbody>
            <tr>
              <td>The table body</td>
              <td>with two columns</td>
            </tr>
          </tbody>
        </table>
      </main>
    </a-skeleton>

    <!-- Vue v-model -->
    <span>Multiline message is:</span>
    <p style="white-space: pre-line">{{ message }}</p>
    <textarea v-model="message" placeholder="add multiple lines"></textarea>

    <!-- v-for -->
    <ul>
      <li v-for="(item, index) in items" :key="item.message">
        {{ parentMessage }} {{ index + 1 }} - {{ item.message }}
      </li>
    </ul>

    <!-- @ event (Event Handling) with v-if -->
    <br />
    <div v-if="isShow">
      <button @click="noClick">給我回去</button>
      <br />Hi ᐠ( ᐛ )ᐟᐠ( ᐖ )ᐟ
    </div>
    <button @click="onClick" v-else>快點按我</button>
    <br /><br />
    <button @mouseover="add">+1</button>
    {{ counter }}
    <br /><br />

    <!-- UI -->
    <p>
      <a-button
        type="primary"
        icon="poweroff"
        :loading="iconLoading"
        @click="enterIconLoading"
      >
        delay 1s
      </a-button>
      <strong v-if="iconLoading"> turning off...</strong>
    </p>

    <a-progress type="circle" width="100px" :percent="percent" />

    <footer>footer</footer>
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from "@/components/HelloWorld.vue";

export default {
  name: "Home",
  components: {
    HelloWorld,
  },
  data() {
    return {
      loading: true,
      message: "add multiline lines",
      parentMessage: "Charms",
      items: [{ message: "Expecto Patronum" }, { message: "Expelliarmus" }],
      isShow: false,
      counter: 0,
      iconLoading: false,
      turnOff: false,
      percent: 0,
    };
  },
  created() {
    setTimeout(() => {
      this.loading = false;
    }, 1000);
  },
  methods: {
    onClick: function () {
      this.isShow = true;
    },
    noClick: function () {
      this.isShow = false;
    },
    add: function () {
      this.counter++;
    },
    enterIconLoading() {
      setTimeout(() => {
        this.iconLoading = true;
      }, 1000);

      setInterval(() => {
        this.percent += 25;
      }, 1000);
      setTimeout(() => {
        this.turnOff = true;
      }, 5000);
    },
  },
};
</script>

<style lang="scss" scoped>
table,
td {
  border: 1px solid #333;
}

thead,
tfoot {
  background-color: #333;
  color: #fff;
}
</style>
