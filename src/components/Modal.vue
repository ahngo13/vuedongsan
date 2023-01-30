<template>
  <div class="black-bg" v-if="isShowModal">
    <div class="white-bg">
      <div v-if="selectedIndex !== undefined">
        <img style="width: 100%;" :src="products[selectedIndex].image"/>
        <h4>{{  products[selectedIndex].title }}</h4>
        <p>{{ products[selectedIndex].content }}</p>
        <button @click="$emit('closeModal')">닫기</button>
        <Discount/>
      </div>
      <div v-else>
        <h4>내용 없음</h4>
        <p>내용 없음</p>
        <button @click="$emit('closeModal')">닫기</button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
    name: 'ModalDiv',
    //props는 수정이 안됨. readOnly
    props: {
        products : Array,
        selectedIndex : Number,
        isShowModal: Boolean,
    },
}
</script>


<style>
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