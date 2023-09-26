<template>
  <div class="box_all">
    <div class="col" v-for="(n, i) in travelList" :key="n">
      <div class="card">
        <img :src="n.img" class="card-img-top" alt="Travel Destination">
        <div class="card-body">
          <h3 class="card-title">{{ n.name }}</h3>
          <p class="card-text">ราคาโต๊ะ: {{ n.price }} บาท</p>
          <h6 class="card-subtitle">*** จำกัด 5 คนต่อ 1 โต๊ะ ***</h6>
          <button class="btn btn-primary" @click="list_local_control(n.name, n.quantity)">จองโต๊ะ</button>
        </div>
      </div>
    </div>
  </div>
</template>


<script setup>

import { ref } from 'vue';

const travelList=ref([
{name: 'ท่าช้าง คาเฟ่',  price:200, img:"https://scontent.fbkk13-2.fna.fbcdn.net/v/t39.30808-6/305202427_500184272111841_8929391628957097856_n.jpg?_nc_cat=107&ccb=1-7&_nc_sid=a2f6c7&_nc_eui2=AeGAHBda0qlZUaus-jQrfXcFmxQOTNjEO12bFA5M2MQ7Xdl_PHIVMqNuVHLipYkNN7J8kiwMIljBimY2BuawICU-&_nc_ohc=H17AuZM0figAX8e2wqG&_nc_ht=scontent.fbkk13-2.fna&_nc_e2o=s&oh=00_AfCTymFnwyAaBVVcRaqt4HU2x67BiW5oR0l0_hrvVopGWA&oe=65128832", quantity: 0 ,
    text_box:'ใครที่เป็นสายชิลล์ สายปาร์ตี้ บอกเลยว่าถ้าไปเชียงใหม่ทั้งทีก็ต้องไปแวะเช็คอินร้านชื่อดังอย่าง “ร้านท่าช้าง” ✨ นั่นเองจ้า ซึ่งร้านนี้เรียกได้ว่าเป็นร้านใหญ่ขวัญใจวัยรุ่นชาวเชียงใหม่เลย มีนักท่องเที่ยวมากมายที่ต้องแวะเวียนกันไปเช็คอินสักครั้ง มีความน่าสนใจอะไร วันนี้บทความนี้จะพาเพื่อนๆ ไปเช็คอินท่าช้างกันแบบ Exclusive เลยจ้า  ถ้าพร้อมแล้วก็ตามมาเลย '
    }])


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