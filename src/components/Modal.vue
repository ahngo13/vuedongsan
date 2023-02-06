<template>
  <div class="black-bg" v-if="isShowModal">
    <div class="white-bg">
      <div v-if="selectedIndex !== undefined">
        <img style="width: 100%;" :src="products[selectedIndex].image"/>
        <h4>{{  products[selectedIndex].title }}</h4>
        <p>{{ products[selectedIndex].content }}</p>
        <select v-model="checkedValue">
          <option value="1">1</option>
          <option value="2">2</option>
          <option value="3">3</option>
          <option value="4">4</option>
        </select><br/><br/>
        <textarea v-model="text"></textarea><br/>
        <!-- @input="month = $event.target.value"와 v-model 같음 -->
        <input v-model.number="month"/>
        <p>체크된 value : {{ checkedValue }}</p>
        <p>메모 : {{ text }}</p>
        <p>{{ month }}개월 선택함 (기본값 1개월) : {{ products[selectedIndex].price * month }}원</p>
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
    data(){
      return {
        month : 1,
        text : '',
        checkedValue : ''
      }
    },
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