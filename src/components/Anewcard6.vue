<template>
  <div class="box_all">
  <div class="col" v-for="(n,i) in travelList" :key="n">
    <div class="card" style="width: 25rem;" >
      <img :src="n.img" class="card-img-top">
      <div class="card-body">
        <h3 class="card-title">{{ n.name }}</h3>
        <p>ราคาโต๊ะ : {{n.price}}</p>
        <h6>***จำกัด 5 คนต่อ 1 โต๊ะ***</h6>

        <a class="btn btn-primary" @click="list_local_control(i.name, i.quantity)"> จองโต๊ะ </a>
      </div>
    </div>
  </div>
</div>

</template>

<script setup>

import { ref } from 'vue';

const travelList=ref([
{name:'Bang Kwang',  price:130,  img:"https://scontent.fbkk13-2.fna.fbcdn.net/v/t39.30808-6/309864222_473114594848997_4975034476894851813_n.jpg?_nc_cat=106&ccb=1-7&_nc_sid=a2f6c7&_nc_eui2=AeFwfKBrICEi01paFfZRztbp14H5fSZXbzzXgfl9JldvPKkBKRf7_vbJM9gd5htsajD5D750AG9_Pp_dU0npXPzk&_nc_ohc=laV55krwxoMAX8z4Q-R&_nc_ht=scontent.fbkk13-2.fna&_nc_e2o=s&oh=00_AfCH9v_s-lLFfZ2KxE3wUFXr4P46AhYeFZkF3p6BYVf9Yg&oe=65126A6A", quantity: 0 ,
    text_box:'ร้านนี้ไม่ได้เป็นเพียงแค่ร้านเหล้าปกติธรรมดา แต่ยังมีความพิเศษที่ทางร้านจัดให้กับลูกค้าในทุก ๆ วัน ไอ้ที่เคยมาที่นี่ต่างพูดเป็นเสียงเดียวกันว่า นี้นักร้องดังนักร้องเด็ด เพลงเพราะ อาหารอร่อย และเป็นร้านที่บรรยากาศดีเหมาะกับการนั่งชิวหรือนั่งดื่มสังสรรค์ในยามค่ำคืนเป็นอย่างมาก'
    },])


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
