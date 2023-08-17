<template>

<Transition name="fade">
  <Modal @closeModal= "모달창열렸니 = false" :원룸들="원룸들" :누른거="누른거" :모달창열렸니="모달창열렸니"/>
</Transition>

  <div class="menu">
    <a v-for="a in 메뉴들" :key="a">{{ a }}</a>
  </div>

  <Discount v-bind="오브젝트" :이름="오브젝트.name" :나이="오브젝트.age"/>

  <Card @openModal="모달창열렸니 = true; 누른거 = $event" :원룸="원룸들[i]" v-for="(작명,i) in 원룸들" :key="작명"/>
  
</template>

<script>
import data from './assets/oneroom.js';
import Discount from './Discount.vue';
import Modal from './Modal.vue';
import Card from './Card.vue';

export default {
  name: 'App',
  data(){
    return{
      오브젝트 : {name : 'Kim', age : 20},
      누른거 : 0,
      원룸들 : data,
      모달창열렸니 : false,
      신고수 : [0,0,0],
      메뉴들 : ['Home','Shop','About'],
      products : ['역삼동원룸','천호동원룸','마포구원룸'],
    }
  },
  methods: {
    increase() {
      this.신고수 += 1;
    }
  },
  components: {
    Discount : Discount,
    Modal : Modal,
    Card : Card,
  }
}
</script>

<style>
.fade-enter-from {
  transform: translateY(-1000px);
}
.fade-enter-active {
  transition: all 1s;
}
.fade-enter-to {
  transform: translateY(0px);
}

body {
  margin: 0
}
div {
  box-sizing: border-box;
}
.discount{
  background: #eee;
  padding: 20px;
  margin: 10px;
  border-radius: 5px;
}

.black-bg {
  width: 100%; height: 100%;
  background: rgba(0,0,0,0.5);
  position: fixed; padding: 20px;
}
.white-bg {
  width: 100%; background: white;
  border-radius: 8px;
  padding: 20px;
}
.room-img{
  width: 50%;
  margin-top: 40px;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

.menu{
  background: darkslateblue;
  padding: 15px;
  border-radius: 5px;
}
.menu a{
  color : white;
  padding: 10px;
}
</style>
