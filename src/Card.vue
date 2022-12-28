<template>
<!-- 축약할 html 복붙 -->
<!-- <div v-for="(a,i) in 원룸들" :key="i"> -->
<!-- 반복문 돌리면 상품 n개(여기서는 6개)를 컴포넌트화 하는 것이고, 그렇지 않으면 상품 하나만을 컴포넌트화 하는 것-->


<div>
  <img :src="원룸.image" class="room-img">
  <h4 @click="$emit('openModal', 원룸.id)">{{ 원룸.title }}</h4>
  <p>{{ 원룸.price }}원</p>

</div>
  
</template>

<script>
export default {
    props : {
        원룸 : Object,

        
    }
}
</script>

<style>

</style>