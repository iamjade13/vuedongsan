<template>


<!-- 데이터 전송 step1 -->
<Modal @closeModal="모달창열렸니=false" :원룸들="원룸들" :누른거 ="누른거" :모달창열렸니="모달창열렸니" />

<!-- Vue if-else 쓰는 법 -->
<div v-if="1 == 2">
  안녕하세요
</div>
<div v-else-if="1 == 3">
  공부하는 거 너무 재밌다ㅎㅎ
</div>  
<!-- <div v-else>
  구라임ㅋ집가고싶다
</div> -->

<div class="menu">
  <a v-for="(a,i) in 메뉴들" :key="i">{{ a }}</a>
</div>

<Discount/>

<button @click="priceSort()">가격순 정렬</button>
<button @click="sortBack()">되돌리기</button>
<!-- 문자열은 v-bind 문법없이 가능 숫자도 문자열 취급-->
<!-- <Discount v-bind="오브젝트"/>  == :이름="오브젝트.name" :나이="오브젝트.age"-->


<!-- 모달창 만들기 --> 
<!-- <div class="black-bg" v-if="모달창열렸니 == true">

  <div class="white-bg">
  <img :src="원룸들[누른거].image" style="width:100%">
  <h4>{{ 원룸들[누른거].title }}</h4>
  <p>{{ 원룸들[누른거]. price}}</p>
  <p>{{ 원룸들[누른거]. content}}</p>
  <Discount/>
  <button @click="모달창열렸니 = false">닫기</button>
  </div>

</div> -->

<!-- 반복문 돌리는 구문 -->
<!--
<div v-for="(작명,i) in products" : key="i">
  <h4>{{ 작명 }}</h4>
  <p>50만원</p>
</div>        
-->

<Card @openModal="모달창열렸니 = true; 누른거 = $event" :원룸="원룸들[i]" v-for="(작명, i) in 원룸들" :key="작명"/>
<!-- $event 대신 i넣어도 잘 뜸 -->
<!-- <Card @click="모달창열렸니 = true" :원룸="원룸들[i]" v-for="(작명, i) in 원룸들" :key="작명"/> -->
<!-- <Card :원룸="원룸들[1]"/>
<Card :원룸="원룸들[2]"/>
<Card :원룸="원룸들[3]"/>
<Card :원룸="원룸들[4]"/>
<Card :원룸="원룸들[5]"/> -->


<!-- <div v-for="(a,i) in 원룸들" :key="i">

  <img :src="a.image" class="room-img">
  < == img :src="원룸들[i].image" class="room-img"> 
  <h4 @click="모달창열렸니 = true; 누른거 = i">{{ a.title }}</h4>
  <p>{{ a.price }}원</p>

</div> -->

<!-- <div>
  <img :src="원룸들[0].image" class="room-img">
  <h4 @click="모달창열렸니 = true">{{ 원룸들[0].title}}</h4>
  <p>{{ 원룸들[0].price }}원</p>
  <button @click="신고수[0]++">허위매물신고</button> 
  <span>신고수 :  {{신고수[0]}} </span>
</div>

<div>
  <img :src="원룸들[1].image" class="room-img">
  <h4>{{ products[1]}}</h4>
  <p>{{ price2 }} 만원</p>
  <button @click="신고수[1]++">허위매물신고</button> 
  <span>신고수 :  {{신고수[1]}} </span>
</div>

<div>
    <img src="./assets/room2.jpg" class="room-img">
    <h4>{{ products[2]}}</h4>
    <p>{{ price2 }}만원</p>
    <button @click="신고수[2]++">허위매물신고</button> 
    <span>신고수 :  {{신고수[2]}} </span>
</div> -->


 
</template>

<script>

import data from './assets/oneroom.js';
import Discount from './Discount.vue';
import Modal from './Modal.vue';
import Card from './Card.vue';


export default {
  name: 'App',
  data(){
    return { 
      원룸들오리지널 : [...data],
      오브젝트 : {name : 'kim', age : 20},
      누른거 : 0,
      원룸들 : data,
      모달창열렸니 : false,
      메뉴들 : ['Home', 'Shop', 'About'],
      price1 : 60,
      price2 : 70,
      스타일 : 'color:red',
      products : ['역삼동원룸', '천호동원룸', '마포구원룸'],
      신고수 : [0,0,0]

    }
  },
  methods: {
    increase(){
      this.신고수 += 1;
    },
    priceSort(){
      this.원룸들.sort(function(a,b){
        return a.price - b.price
      })
      
    },
    sortBack(){
      this.원룸들 = [...this.원룸들오리지널];
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
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;

}

.menu {
  background: darkslateblue;
  padding : 15px;
  border-radius : 5px;
}

.menu a {
  color: white;
  padding: 10px;
}

.room-img {
  width: 100%;
  margin-top: 40px;
}

body {
  margin : 0
}

div {
  box-sizing: border-box;
}

.black-bg {
  width: 100%; height: 100%;
  background: rgba(0,0,0,0.5);
  position: fixed; padding: 20px;
}
.white-bg {
  width: 100%; background:white;
  border-radius: 8px;
  padding: 20px;
}

.discount{
  background: #eee;
  padding: 10px;
  margin:10px;
  border-radius: 5px;
}
</style>
