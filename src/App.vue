<template>
  <div class="group1-9 df fd-c" id="app">
    <div class="df fg1 fd-c lg-fd-r">
      <div class="box box1 fg1" @click="changeColors()"><span>1</span></div>

      <div class="fg2 lg-fg1 df fd-cr lg-fd-c">
        <div class="box box2 fg1" @click="changeColors()"><span>2</span></div>
        <div class="df fg1">
          <div class="box box3 fg1" @click="changeColors()"><span>3</span></div>
          <div class="box box4 fg1" @click="changeColors()"><span>4</span></div>
        </div>
      </div>
    </div>

    <div class="df fd-c fg1">
      <div class="only-mobile box box7 fg1" @click="changeColors()">
        <span>7</span>
      </div>

      <div class="df fg2">
        <div class="fg1 df fd-c">
          <div class="box box5 fg1" @click="changeColors()"><span>5</span></div>
          <div class="box box6 fg1 lg-fg2" @click="changeColors()">
            <span>6</span>
          </div>
        </div>

        <div class="only-desktop box box7 fg1" @click="changeColors()">
          <span>7</span>
        </div>

        <div class="fg1 df fd-c">
          <div class="box box8 fg1 lg-fg2" @click="changeColors()">
            <span>8</span>
          </div>
          <div class="box box9 fg1" @click="changeColors()"><span>9</span></div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
// actually, I believe this would work as an static page, but the instructions said "use a framework" so I am using Vue3

export default {
  name: "App",
  components: {},
  methods: {
    pickColor() {
      var hue = Math.random() * 360;
      // saturation has a lower bound so colors are not too dim
      var saturation = 20 + Math.random() * 80;
      // limit lightness range so colors are not too dark nor too light
      var lightness = 20 + Math.random() * 30;
      return `hsl(${hue}, ${saturation}%, ${lightness}%)`;
    },
    changeColors() {
      for (let i = 1; i < 10; i++) {
        var box_name = `box${i}`;
        var boxes = document.getElementsByClassName(box_name);
        //this is saved on a var so box7 has always the same color
        var randomColor = this.pickColor();
        for (var box of boxes) {
          box.style.backgroundColor = randomColor;
        }
      }
    },
  },
};
</script>

<style>
body {
  font-family: Arial, sans-serif;
}

.box {
  margin: 5px;
  color: white;
  text-align: center;
  display: flex;
  align-items: center;
  justify-content: center;
  font-weight: bold;
  user-select: none;
}

.box1 {
  background-color: dodgerblue;
}

.box2 {
  background-color: crimson;
}

.box3 {
  background-color: darkgoldenrod;
}

.box4 {
  background-color: indianred;
}

.box5 {
  background-color: darkviolet;
}

.box6 {
  background-color: darkturquoise;
}

.box7 {
  background-color: teal;
}

.box8 {
  background-color: slateblue;
}

.box9 {
  background-color: darkslategray;
}

.group1-9 {
  height: 500px;
}

.fd-cr {
  flex-direction: column-reverse;
}

.fd-c {
  flex-direction: column;
}

.df {
  display: flex;
}

.fg1 {
  flex-grow: 1;
}

.fg2 {
  flex-grow: 2;
}

.only-desktop {
  display: none;
}

span {
  display: inline-block;
  vertical-align: middle;
}

@media screen and (min-width: 600px) {
  .lg-fg1 {
    flex-grow: 1;
  }

  .lg-fg2 {
    flex-grow: 2;
  }

  .group1-9 {
    width: 600px;
  }

  .lg-fd-c {
    flex-direction: column;
  }

  .lg-fd-r {
    flex-direction: row;
  }

  .only-desktop {
    display: flex;
  }

  .only-mobile {
    display: none;
  }
}
</style>
