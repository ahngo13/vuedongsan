<template>
  <div class="black-bg" v-if="isShowModal">
    <div class="white-bg">
      <h4>상세페이지임</h4>
      <p>상세페이지 내용임</p>
      <button @click="isShowModal = false">닫기</button>
    </div>
  </div>
  <div v-for="item, index in products" :key="index">
    <img class="room-img" :src="item.image"/>
    <h4 @click="isShowModal = true">{{ item.title }}</h4>
    <p>{{ item.price }}만원</p>
    <button @click="()=>increase(item)">허위매물 신고</button><span>신고수 : {{item.count}}</span>
  </div>
</template>

<script>

import products from './oneroom';

export default {
  name: 'App',
  data(){
    return {
      modalData : {
        modalTitle : '',
        modalDesc : '',
      },
      isShowModal: false,
      products
    }
  },
  methods: {
    increase(item){
      item.count++;
    },
  },
  components:{}
}
</script>

<!--
  동적 UI 만드는 법:
  0.HTML CSS로 디자인 해두셈 (기본)
  1.UI의 현재 상태를 데이터로 저장해둠
  2.데이터에 따라 UI가 어떻게 보일지 작성
-->


<style>

.room-img{
  width: 100%;
  margin-top: 40px;
}

body{
  margin: 0;
}
div{
  box-sizing: border-box;
}

.black-bg{
  width: 100%; height: 100%;
  background: rgba(0, 0, 0, 0.5);
  position: fixed; padding: 20px;
}
.white-bg{
  width: 100%; background: white;
  border-radius: 8px;
  padding: 20px;
}
</style>