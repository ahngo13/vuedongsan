<template>
  
  <Modal @closeModal="isShowModal = false;" :products="products" :selectedIndex="selectedIndex" :isShowModal="isShowModal"/>
  <Card @openModal="isShowModal = true; selectedIndex = index" :item="item" v-for="item, index in products" :key="index"/>
  <Discount />

</template>

<script>

import products from './oneroom';
import Discount from './components/Discount.vue';
import Modal from './components/Modal.vue';
import Card from './components/Card.vue';

export default {
  name: 'App',
  data(){
    return {
      selectedIndex : undefined,
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
  components:{
    Discount,
    Modal,
    Card
  }
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
  text-align: center;
}
div{
  box-sizing: border-box;
}


</style>