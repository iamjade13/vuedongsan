<template>

  <div class="black-bg" v-if="모달창열렸니 == true">
  
  <div class="white-bg">
  <img :src="원룸들[누른거].image" style="width:100%"> 
  <h4>{{원룸들[누른거].title}}</h4>
  <p>{{ 원룸들[누른거].content}}</p>
  <!-- <input @input="month = $event.target.value">-->
  <!-- <input type="range" min="1" max="12"> 문자 입력 못하게 편법으로 제한두기 -->
  <input v-model="month">
  <!-- <select v-model ="month">
    <option>10</option>
    <option>20</option>
    <option>30</option>
  </select> -->

  <p> {{ month }}개월 선택함 : {{ 원룸들[누른거].price * month}}원</p>
  
  <button @click="$emit('closeModal')">닫기</button>
  
  <Discount/>


  <!-- <button @click="모달창열렸니 = false">닫기</button> -->
  <!-- props는 read-only라 받아온거 수정하면 안됨!! -->
  </div>

</div>
</template>

<script>
import Discount from './Discount.vue';

export default {
    name : 'Modal',
    data() {
      return {
        month : 1,
        date : 123
      }
    },
    watch : {
      month(a){
        if(isNaN(a) == true) {
          alert('숫자만 입력해주세요')
          this.month=1;
        }
      },
    },
    props : {
      // 데이터 전송 step2
      원룸들 : Array,
      누른거 : Number,
      모달창열렸니: Boolean,
    },

    components : {
      Discount : Discount,
    }
}
</script>

<style>

</style>