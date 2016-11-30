<template>
  <div class="carousel-model">
    
    <ul class="carousel-content" :style="{'transform': 'translate3d(' + -(index * 700) + 'px, 0, 0)'}">
      <li v-for="carousel in carousels"><a :href="carousel.url" target="_blank"><img :src="carousel.img" alt=""></a></li>
    </ul>
    
    <ul class="slider-bar">
      <li
        bar="bar"
        v-for="(carousel, $index) in carousels"
        :class="{'on': $index === index}"
        @click="go($index)"
        @mouseover="end"
        @mouseout="start">
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'carousel',
  data () {
    return {
      index: 0,
      timer: '',
      carousels: [
        {
          url: 'http://www.baidu.com',
          img: './static/1.jpg'
        },
        {
          url: 'http://www.baidu.com',
          img: './static/2.jpg'
        },
        {
          url: 'http://www.baidu.com',
          img: './static/3.jpg'
        }
      ]
    }
  },
  methods: {
    go (i) {
      this.index = i
    },
    end () {
      clearInterval(this.timer)
    },
    start () {
      this.timer = setInterval(() => {
        this.index = this.index >= 2 ? 0 : this.index += 1
      }, 3000)
    },
    mounted () {
      //启动定时器
      this.start()
    },
    destory () {
      this.end()
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

img, ul, li{
  padding: 0;
  margin: 0;
}
li {
  list-style: none;
}
.carousel-model {
  position: relative;
  width: 700px;
  height: 510px;
  margin: 50px auto;
  overflow: hidden;
  border: 1px solid #ccc;
  /*  border-radius: 6px; */
  /* background: #000; */
}
.carousel-content {
  width: 2100px;
  height: 510px;
  margin-left: 0;
  transition: transform .3s cubic-bezier(.86,0,.07,1),-webkit-transform .3s cubic-bezier(.86,0,.07,1);
      transform: translate3d(0, 0, 0);
}

.carousel-content li {
  float: left;
  width: 700px;
  height: 510px;
  margin: 0;
}

.carousel-content a {
  position: relative;
  display: inline-block;
  width: 700px;
  height: 510px;
  margin: 0;
}

.slider-bar {
  position: absolute;
  left: 312px;
  bottom: 0px;
  overflow: hidden;
  padding: 2px 5px;
}

.slider-bar li {
  float: left;
  cursor: pointer;
  width: 18px;
  height: 18px;
  margin: 2px 2px;
  background: url(http://static.hdslb.com/images/base/icons.png) -855px -790px no-repeat;
}

.slider-bar li:hover {
  background-position: -919px -790px;
}

.slider-bar li.on {
  background-position: -855px -727px;
}

.slider-bar li.on:hover {
  background-position: -855px -727px;
}

.carousel-content img {
  display: inline-block;
  margin: 0;
  width: 700px;
  height: 510px;
  border: none;
}

</style>