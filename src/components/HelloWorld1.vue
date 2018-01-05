<template>
  <div class="hello">
    <div id="contain">
      <div class="contain" @mousedown="mousedown" @mousemove="mousemove" @mouseup="mouseup" @mouseover="mouseover">
        <div class="cube1 slide">
          <div class="contain">
            <!-- <div class="cube1 slide">1</div>
            <div class="cube2 slide">2</div>
            <div class="cube3 slide">3</div>
            <div class="cube4 slide">4</div>
            <div class="cube5 slide">5</div>
            <div class="cube6 slide">6</div> -->
          </div>
        </div>
        <div class="cube2 slide">
          <div class="contain">
            <!-- <div class="cube1 slide">1</div>
            <div class="cube2 slide">2</div>
            <div class="cube3 slide">3</div>
            <div class="cube4 slide">4</div>
            <div class="cube5 slide">5</div>
            <div class="cube6 slide">6</div> -->
          </div>
        </div>
        <div class="cube3 slide">
          <div class="contain">
            <!-- <div class="cube1 slide">1</div>
            <div class="cube2 slide">2</div>
            <div class="cube3 slide">3</div>
            <div class="cube4 slide">4</div>
            <div class="cube5 slide">5</div>
            <div class="cube6 slide">6</div> -->
          </div>
        </div>
        <div class="cube4 slide">
          <div class="contain">
            <!-- <div class="cube1 slide">1</div>
            <div class="cube2 slide">2</div>
            <div class="cube3 slide">3</div>
            <div class="cube4 slide">4</div>
            <div class="cube5 slide">5</div>
            <div class="cube6 slide">6</div> -->
          </div>
        </div>
        <div class="cube5 slide">
          <div class="contain">
            <!-- <div class="cube1 slide">1</div>
            <div class="cube2 slide">2</div>
            <div class="cube3 slide">3</div>
            <div class="cube4 slide">4</div>
            <div class="cube5 slide">5</div>
            <div class="cube6 slide">6</div> -->
          </div>
        </div>
        <div class="cube6 slide">
          <div class="contain">
            <!-- <div class="cube1 slide">1</div>
            <div class="cube2 slide">2</div>
            <div class="cube3 slide">3</div>
            <div class="cube4 slide">4</div>
            <div class="cube5 slide">5</div>
            <div class="cube6 slide">6</div> -->
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
/*每个立方体都要有一个容器包裹,立方体大小为父容器的一般*/
export default {
  name: "HelloWorld1",
  comments: {},
  props: {
    childDeep: {
      type: Number,
      default: 3
    }
  },
  data() {
    return {
      currentX: 0,
      currentY: 0,
      rotX: 0,
      rotY: 0,
      divLis: []
    };
  },
  methods: {
    generId() {
      let id = "cube" + new Date().getTime();
      return id;
    },
    mousedown(e) {},
    mousemove(e) {},
    mouseup(e) {},
    mouseover(e) {},
    creatChild(dom) {
      dom = document.getElementById("contain");
      dom.innerHTML = "";
      let deep = this.childDeep*6;
      let innerCreat = function(pDom) {
        let innerPdom = document.createElement("div");
        innerPdom.classList.add("contain");
        innerPdom.style.transformOrigin = "50% 50%" + pDom.offsetWidth / 4 * -1 + "px";
        innerPdom.style.transform = "rotateX(60deg) rotateY(60deg)";
        for (let i = 0; i < 6; i++) {
          let div = document.createElement("div");
          div.classList.add("slide", "cube" + (i + 1));
          if(i == 2){
            div.style.transformOrigin = "50% 0%" + innerPdom.offsetWidth / 2 * -1 + "px";
          }
          innerPdom.appendChild(div);
          if(deep>0){
              deep--;
            innerCreat(div);
          }
        }
        pDom.appendChild(innerPdom);
      };
      innerCreat(dom);
    }
  },
  computed: {},
  created() {},
  mounted() {
    // this.generId();
    this.creatChild();
  },
  watch: {}
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style>
.hello {
  width: 100%;
  height: 80%;
  position: relative;
}

#contain {
  width: 500px;
  height: 500px;
  background-color: #ebeef5;
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
}

.contain {
  width: 50%;
  height: 50%;
  position: relative;
  top: 25%;
  left: 25%;
  /* transform: rotateX(60deg) rotateY(60deg); */
  transform-style: preserve-3d;
  /* perspective: 20000px; */
  /* transform-origin: 50% 50% -125px; */
  /*js控制为宽度的一半*/
}

.slide {
  width: 100%;
  height: 100%;
  text-align: center;
  position: absolute;
  /* line-height: 250px; */
  box-sizing: border-box;
  border: 1px solid #000;
  /* backface-visibility:hidden; */
}

.cube1 {
  left: 0;
  top: 0;
  background-color: rgba(255, 102, 102, 0.75);
  transform: rotateX(0deg) rotateY(0deg);
  transform-origin: 50% 50% 0px;
}

.cube2 {
  left: -100%;
  top: 0;
  background-color: rgba(179, 255, 102, 0.75);
  transform: rotateY(-90deg);
  transform-origin: right;
}

.cube3 {
  left: 0;
  top: 0;
  background-color: rgba(102, 255, 255, 0.75);
  transform: rotateY(180deg);
  /* transform-origin: 50% 0% -125px; */
  /*js控制为父元素宽度的一半*/
}

.cube4 {
  left: 100%;
  top: 0;
  background-color: rgba(178, 102, 255, 0.75);
  transform: rotateY(90deg);
  transform-origin: 0% 0% 0px;
}

.cube5 {
  left: 0;
  top: -100%;
  background-color: rgba(164, 214, 27, 0.75);
  transform: rotateX(90deg);
  transform-origin: bottom;
}

.cube6 {
  left: 0;
  top: 100%;
  background-color: rgba(184, 33, 121, 0.75);
  transform: rotateX(-90deg);
  transform-origin: top;
}
</style>

