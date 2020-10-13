<template>
  <div class="area">
    <div class="msg-container">
      <div id="slider" ref="slider">
        <div
          v-for="(item, index) in content"
          :key="index"
          class="msg-col"
          :id="index + 1"
          :ref="index + 1"
        >
          <h1>{{ item.title }}</h1>
          <p>{{ item.paragraph }}</p>
        </div>
      </div>
    </div>

    <div class="cardp">
      <div id="photos" ref="photos">
        <div v-for="(item, index) in content" :key="index" class="img-card">
          <img :src="item.photo" class="image" :alt="item.photo" />
        </div>
      </div>
    </div>

    <div class="controller">
      <div v-for="(item, index) in content.length" :key="index">
        <div
          @click="click($event)"
          :id="index + 1"
          class="line"
          :style="{ height: num + 'px' }"
        ></div>
      </div>
      <div ref="active" id="active" :style="{ height: num + 'px' }"></div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Slider",
  data() {
    return {
      s: 0,
      percent: 100,
      num: 320 / this.content.length,
      percent1: 100 / this.content.length,
    };
  },
  props: {
    content: {
      required: false,
    },
  },
  methods: {
    click(e) {
      if (e.target.id == 1) {
        this.s = e.target.id;
        this.$refs.slider.style.transform = "translateX(0)";
        this.$refs.photos.style.transform = "translateX(0)";
        this.$refs.active.style.top = "0px";
      } else if (e.target.id > 1) {
        this.s = e.target.id;
        let d = e.target.id * this.num - this.num;
        let p = e.target.id * this.percent - this.percent;
        let p1 = e.target.id * this.percent1 - this.percent1;
        this.$refs.slider.style.transform = "translateX(-" + p1 + "%" + ")";
        this.$refs.photos.style.transform = "translateX(-" + p + "%" + ")";
        this.$refs.active.style.top = d + "px";
      } else {
        console.log(err);
      }
    },
  },
  // mounted() {
  //   setInterval(() => {
  //     if (this.$refs.active.style.top != 320 - this.num + "px") {
  //       this.$refs.slider.style.transform +=
  //         "translateX(-" + this.percent1 + "%" + ")";
  //       this.$refs.photos.style.transform += "translateX(-" + 100 + "%" + ")";

  //       this.$refs.active.style.top = "";

  //       if (this.s == 0) {
  //         this.s++;
  //         let scrl = this.num;
  //         this.$refs.active.style.top += scrl + "px";
  //         this.s++;
  //         console.log(this.s);
  //       } else if (this.s >= 1) {
  //         this.s++;

  //         let scrl = this.s * this.num - this.num;
  //         this.$refs.active.style.top += scrl + "px";
  //         console.log(this.s);
  //       }
  //       console.log(this.$refs.active.style.top);
  //     } else if (this.$refs.active.style.top == 320 - this.num + "px") {
  //       this.$refs.slider.style.transform = "translateX(0)";
  //       this.$refs.photos.style.transform = "translateX(0)";
  //       this.s = 0;
  //       this.$refs.active.style.top = "0px";
  //       console.log(this.$refs.active.style.top);
  //     } else {
  //       this.$refs.slider.style.transform = "translateX(0)";
  //       this.$refs.photos.style.transform = "translateX(0)";
  //       this.s = 0;
  //       this.$refs.active.style.top = "0px";
  //       console.log(this.$refs.active.style.top);
  //     }
  //   }, 5000);
  // },
};
</script>

<style scoped>
* {
  margin: 0;
  padding: 0;
  font-family: sans-serif;
}

.area {
  width: 100%;
  height: 50vh;
  position: relative;
  padding-top: 30px;
  box-sizing: border-box;
}

.cardp {
  width: 100vw;
  height: 50vh;
  position: absolute;
  top: 0;
  overflow: hidden !important;
}

.img-card {
  height: 50vh;
  width: 100vw;
}

.image {
  display: block;
  margin-left: auto;
  margin-right: auto;
  width: 100vw;
  height: 50vh;
  object-fit: cover;
}

#photos {
  display: flex;
  transition: 1s;
}

.msg-container {
  width: 500px;
  height: 280px;
  position: absolute;
  left: 38%;
  top: 50%;
  transform: translateY(-100px);
  overflow: hidden;
  z-index: 90;
}

#slider {
  display: inline-flex;
  transition: 1s;
}

.msg-col {
  width: 500px;
  height: 280px;
}

.msg-col h1 {
  color: #ffffff;
  font-size: 80px;
  font-weight: 100;
  margin: 10px 0;
}

.msg-col p {
  color: #dddddd;
  font-size: 15px;
  line-height: 25px;
}

.controller {
  width: 1px;
  height: 320px;
  display: block;
  background: #c0c0c0;
  position: absolute;
  top: 55%;
  right: 50px;
  transform: translateY(-50%);
}

.line {
  width: 10px;
  cursor: pointer;
  transform: translateX(-50%);
}
#active {
  width: 5px;
  border-radius: 10px;
  background: #ffffff;
  position: absolute;
  top: 0;
  transform: translateX(-50%);
  transition: 0.5s;
}

@media only screen and (min-width: 701px) and (max-width: 1180px) {
  .msg-container {
    width: 285px;
  }

  .msg-col {
    width: 285px;
  }

  .msg-col h1 {
    font-size: 50px;
  }

  .msg-col p {
    font-size: 16px;
  }

  .controller {
    z-index: 99;
    top: 50%;
  }
}
@media only screen and (min-width: 451px) and (max-width: 750px) {
  .msg-container {
    width: 285px;
    left: 30%;
  }

  .msg-col {
    width: 285px;
  }

  .msg-col h1 {
    font-size: 50px;
  }

  .msg-col p {
    font-size: 16px;
  }

  .controller {
    z-index: 99;
    top: 50%;
  }
}
@media only screen and (min-width: 321px) and (max-width: 450px) {
  .msg-container {
    width: 275px;
    left: 15%;
  }

  .msg-col {
    width: 275px;
  }

  .msg-col h1 {
    font-size: 40px;
  }

  .msg-col p {
    font-size: 14px;
  }

  .controller {
    z-index: 99;
  }
}
@media only screen and (max-width: 320px) {
  .msg-container {
    width: 220px;
    left: 16%;
  }

  .msg-col {
    width: 220px;
  }

  .msg-col h1 {
    font-size: 40px;
  }

  .msg-col p {
    font-size: 14px;
  }

  .controller {
    z-index: 99;
    right: 30px;
  }
}
</style>
