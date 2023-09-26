<template>
  <div class="box_all">
    <div class="col" v-for="(destination, index) in travelList" :key="index">
      <div class="card">
        <img :src="destination.img" class="card-img-top" alt="Travel Destination">
        <div class="card-body">
          <h3 class="card-title">{{ destination.name }}</h3>
          <p class="card-text">ราคาโต๊ะ: {{ destination.price }} บาท</p>
          <h6 class="card-subtitle">*** จำกัด 5 คนต่อ 1 โต๊ะ ***</h6>

          <button class="btn btn-primary" @click="reserveTable(destination.name, destination.quantity)">จองโต๊ะ</button>
        </div>
      </div>
    </div>
  </div>
</template>

<script setup>

import { ref } from 'vue';

const travelList = ref([
{name:'ตะวันแดง',    price:275, img:"https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQWfz4OsyE9JTao17DxBA95W3TxXn2nLusxPuBDcIpw0XoXIU6zRlfQxjs8p1gO_cP7LwY&usqp=CAU", quantity: 0 ,
    text_box:'เป็นสถานบริการด้านความบันเทิงศิลปวัฒนธรรม สามารถสัมผัสโชว์วัฒนธรรม 4 ภาค ตระการตา เฮฮา ครื้นเครงกับก็อปปี้โชว์ สนุกสุดๆ กับวงดนตรี นักร้อง ครบครันทุกแนวเพลง ไม่ว่าจะเป็นเพื่อชีวิต สตริง สากล จนถึงลูกทุ่ง หมอลำ และคำเมืองที่ร้อยเรียง ขยับจังหวะสู่ความ สนุกสุดเหวี่ยงอย่างไม่ขาดตอน'
    },
]);

</script>


<style scoped>
.card {
  width: 18rem;
  margin: 20px;
  border: 1px solid #ddd;
  border-radius: 10px;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
}

.card-img-top {
  height: 200px;
  object-fit: cover;
  border-top-left-radius: 10px;
  border-top-right-radius: 10px;
}

.card-body {
  padding: 20px;
}

.card-title {
  font-size: 1.5rem;
  margin-bottom: 10px;
}

.card-text {
  font-size: 1.2rem;
}

.card-subtitle {
  font-size: 1rem;
  color: #888;
  margin-top: 10px;
}

.btn-primary {
  background-color: #007BFF;
  border: none;
  border-radius: 5px;
  color: #fff;
}

.btn-primary:hover {
  background-color: #0056b3;
}

.box_all {
  display: flex;
  flex-wrap: wrap;
  justify-content: center;
  align-items: center;
  margin: 30px auto;
}
</style>