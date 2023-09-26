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
    {name:'สุนทรารมณ์',   price:120, img:"data:image/jpeg;base64,/9j/4AAQSkZJRgABAQAAAQABAAD/2wCEAAoHCBUVFRgVFRUYGBgaGRgYHBoaGhgYGBoYGBgZGhgaGBgcIS4lHB4rIRgYJjgmKy8xNTU1GiQ7QDs0Py40NTEBDAwMEA8QHhISHDQrJCs0NDQ0NDE0NDQ0NDQ0NDQ0NDQ0NTQ0NDE0NDQ0NDQ0ND00NDQ0NDQ0NDQ0NDQ0NDQ0NP/AABEIAMIBAwMBIgACEQEDEQH/xAAcAAACAgMBAQAAAAAAAAAAAAAAAQIDBAUGBwj/xAA/EAACAQIEAwUFBgMGBwAAAAABAgADEQQSITFBUWEFBiJxgTKRobHBBxNCctHwUsLhFCRTYoKSI0Rjk6LS8f/EABkBAQEBAQEBAAAAAAAAAAAAAAABAgMEBf/EACcRAQEAAgICAQMDBQAAAAAAAAABAhEhMQMSQQQiURNxsRQyYYGR/9oADAMBAAIRAxEAPwDhKiLxosv5SfpKxkBFndN9x++QmXnH4cQfUE/OVMWuLVEY32NrHz+fpObrWLUJJ0em45MLfOY1ROaW6qdJsK+GfjSpt+U2mA9O34HXyNxNuTHbzPrIWlreZ9ZWYCIgIEx5Da8BWgRHGBAiBGFhaSAhEbQAk4TKoxXkjFAV4QMUugXjQfEERSScPOZs0svKoGOI6QvKGTJHaQvAmXQgJISIkppkQhCRRCEIBC8ImEIcIs0IHZVKVY70aZ9G/mmvrUnF81BLbmxUacfLS8yhSpf4db/Y/wD7yqrQThTq+oYfWZldLEXoCx/4Djyb+s17qBfSqvntM77tAP8AmNtbX34yh7cHreoP6SyM5Wte56n1EqmVW/O3qJjysopvrNguHLJmA0Gh6ekwES95k4auydRsRz6QqrEIAdJUJYdTJpTvDN2rCR5J0eA7qYipYlMini+htzyDX32m+odw0t46zH8qBR8SYNx54Yj5T0Ov3BQ+xXYH/Mgb4giaDtTuliaILZQ6D8Sa2HVSLj3SXU7WcuZuYteUyGWVkSivXlFrLSJEzKoG8acY4KYCbc+fzkZJ9/QSMRq9iDbQEGliILHCEqCEIQCEIQCEIQCEIQOzKPxq0/8At4f6NKHT/qj0VB8rzUN2w/BaY/0KT75U/atY7PbyCj6Saa23qU/CPGBpsFXTkNpRVpsNQ5/2j6CaY9o1/wDFb3iH9uqneo0iWxk4gn+In0tMI7xvXc7sTIKZdItoiTr09r7yNKqFvzkqa3MSIyuzMG1RgiKWdjoPqTwA3vPRuxewKWGXObPUtcudl55AfZHXf5SfdbsmnhcP99WIV6gBYtplQ2Kp0J0J62HCbenizVpu2GUPa6hmOVGYDVQNzuNwBrvNJVeHfOLrqOmo98y0p3F5x3d7tPF1KzU89guZnDAMwysAypyNzbkBw0sejx1dXp4qkUv93SDtdiM2YFgFsL7Kdb7262sTTYJTvre/lDJac5X7RrU8NRrJkFLLRGWxY+K4dSb3GUBddzeR7Rer9/iMOHYg0TWQNwAUqVubH2mBHVR1g0o7191lqqatFQtQalRoH/RvnPNHQjee09hVmfDU3fcoONyRsCfPecF387LFOtnUWWoM3+oe18wffON+3KT4v8uk+6fs48yJEm0iZ0ZRIgu8DFeZU3G0hLH+sheWLRaJoXiMRNiEISghCEAhCEAhCEAhCECwwEDvCZBARrGRNAlidZWJam0VGUaYyLYeI3Ppfj++E3fdTs0VsTTQ6jNmYcMiAswPna3rOepT0L7Mqd8S5PCk9vV6Y/WSTUW13Xa2BD4asp4qx9QAR8phfZ5hL4d1HCoT71X9J0j4VnR0QgMylbm9hmBBOkxe7HYFXC5lNRShuTlvckiw3GlppHL9idnZMfXQLdi1U35ZiWAv7pt8X2G/3lSqFpMr4Y0yHJDIQTrYKSVOm3IcpuaGHWnijlAGbU3uSfDzOvGblhZSANQDYddbRKWPNP7IlTDf2JEqsqpnNT7vIGZXz5EL7MTpcgi143wlasyNWwqqQjKXat4vFdWRhTADAqb22uektqd5axqmmyZW8YUAKoJynLpUIbe215Dsp8TVqF3DoinxBmbU2uLKyAcRqOc0y2VBLIF8OgtZVKqANgASZzP2g0L4ZW4q492ot8ROvYTlftAqAYYD+JwB8T/LOHn6n7x08ff+q8mcayBEsqbyuaRExRmKA2290jJjY/vjImApEyVpGaQQhCFEIExXhDhFHCiK8cLwFeEd4RtFnGCxrv74hxmVPhJcZHhJDeaCJlqbSq8vyjKDceUmwU21nf8A2aYkLiQD+NHT10f+SefqdZtuxMc1KojqbFWDDzBuL9Jq9Mx9GYNwCfK81WK73UlbKis4va4Nh6aR9nY2nWprVGqOuqnh/EreRBBEy2qUkAcIigbEhV25W36Sdqx61CtUrJXRMqgLpUIUnpbUibouQ9jsVv6iaar3gW2hA1tY2Wx00JJOviXSxOo0iqdu0CAQ5e9rFQxuCL6ZRtb3cZZC0YvL94zFyNhlWw0A/EQM17ltL21mvyorMy57kWOYs2a2xuxJFteW/lbGq95cN4iMxtf8Li5DhLC9rnMfgeUoodqCo9glkJsrE3u2XMVIvpprcXBBGutpplngk8J539pGNu60v4BmPmdvhr/qncdodopQR6rnwroFvbO9rhR9eQBM8Y7X7QetUeo5uzEk+vLp0nLLD2st+GsbrbXOZExsZC8tSUGKORkaTXjIXk0MrgORkopoKEISoIWgISKIRRwCFoQhBaEWaEC1ePlAbQXYwtp6zKnykucjyjHGaBMjCUc7hdf6THnRd0MF95VNwSFRmNvzIuvS7CTK6m3PyZWY3S4dgIV0zKee/wADNJWotTbK3oRsR0nptLs8nNltZRe5IF77AcybH3Gc73i7NuCbWPXQgyY262+V4fq88fJ659Vb3N7zf2c5HuabnxAbq22deZtuOI8hPQMflemj03zI11zJdzmcWzBd7rvbQgj0PhaMR0tNz2N3ir4dr03ZeY3B/Mp0PqJt9bb1ij2VUIYlsgObKpy5kBLlP4gCt0Isd066OtgyLgZCPANWIsEJKAFRwJPvnL4b7SCRarRRuqlkJ8/aHulj/aFR4YbXrUv8Akozq2EKsWNHCszG5L1XuTwNihjq10w1q2JZFIQilQpDYG1yAQLk5VGYgAAWHXl+0e/dd7ikiUuqr4/973IPlachicW9RizsWJNySSST1J1MDad5O8L4l8zeFBcIg9lQfmTxPH3AaBmkmMqMgDIGSMiZFk0IoyIoaNN4jvCBmQESMnTQscqgknYAXJ9BMt+yawsGRhe1r2G4JHHTQHflG5FktYRimcvZVTituGumoIFvPX5zEdLSzKXouNnauOFoSso2jvHIwpwhCELLCShCpj2TA7esdvBfr9IiNB6zIlxH74Rc4x7X75SIOnrNBmdZ3HxBR6lvxUynozKf5ZyU3fd7E5HY3toPn8pLeHm+p9v0769vWldamUoAAro7gaaKDrb0PqZjdqdlZlfdvEb6jOCbZQCdH0I3tx1mpw9cG2tgePQ7zbP2i6+GoVKtcZ7hT5ludr++ameN4r5HiymdvtOd9vJ+16GSq67anQ6HexuOGxmGGmd25iM9Z35kn3sT9Zrofbw/ti0tIGpEiliFGpJAA5k6CZGNwTUiFYgkqG0zWsdNyBfUHblDdVJiOcVRtbiUkRippaCRItIQBudN43BG/wAweJHDqDIqEGgTC8KBEYwYjMgjIikuAmhmdkUXaqoRM7bhToDYa63FtOs7VuyMU4RjhkzZFUlzTF2DOxIUX0IG5AOrAb66f7P0/vlPrnHvRv0ntuG7NA1bceRHGwv03mcsd1PfKXUeUV+wMUb3SkNds17XuR+G4469JyXbnZz0nGcC518N7Wso3sJ9D4ns9SCQq5jbpci5F/1nkf2j0QChsA3iDW/0kfM+4zMxmNW55XivPzFJsJCdAoQhAIQBhCCEIQLi3hA6kxHhK4TKr19pvIyHD1kQxgGmgS5HK+Ibg/rKRJE8JlLNzTsOyu1Ay6HXiOI/pLe1ccQhF7DfpOLvbbQ89jJPUY+0zHzJPzj1eH+hxmftKlUe5JkZARzT3Sa4ZfZtULWRiNA6G1i2xBFgNSdNhPScThMPiUAPiUt4WUjODmtludjtcHnteea9j0y1emBbNnUqGNlZgQVQnhmIC3/zS6+Iw7m+enUF817q1yCCSPImx66SpZyy+3+774dtw6MRlZTfc2UOPwm4t6c9JpHQi4IsRoQdwRwnZ9ld7l1TE08yto7oPEUJJKspO3ibY2ANgJyWKcM7MqhQWYhRsASSAOklWI4emp9p1XoQx+IFvjwjq0EAJFRD0s9z5eG3vtKDFJra7/wCIrQvJ1EymxI47FWGhI3GnD68ZdCEI4SaDHH4ed//ALGo09YhtvLKYAYZtr62105iQdJ3Fb+90vzge8EWnvGPWqyj7p1Q7ksubTkBtPAezHXDVqVYHMgdWNuQNzYnpznrvYnealiVB1VgCCpI02ueo0v6y+zN4bjDYFlIepWqO++rZUvqNEQAWtwN5519qVHwq/J7f+O/wnoVXGo4HiBGYG9wQbdRPP8A7RXzUCeIdfOxBsb/AL+BnPLL7oR5Y0hJtIGdIqJhCEqgQmVhqVJjZ6jJ1yZhfrZ7/CY7qAdCD1F/qAYRGEIQHaX4bCs+cjQKjvf8i5iPMylZdScWILsv5QDcEW1OYcyLSWtTSgmSRbnloT7gTb4WhVVQfCSRbcgKb+VzIqZUMRsZEGSaAZoZpGXYbDs7BVFySAPMmwgQvCbPtLsCvQRXqUyisxQEldSAToAb2sDraxmb2N3cavSq1Ayj7tcxBNiQTYZRxMlumpLemhRiCCNOvKev4PvTh3wyPiClylmzqGOddGypubkX05ieQ1ksSOUirGJWLHbdu96sOwK4fCUVP+I9OmXvzVctgepv5TiiZEvAmRZCLREx3hLA6bAG5Fxyvb42kqrqdkseeYmUlo7y6NiK0kpHEE+RA+hluHS5Gl5m1ZN1mYfsWs9J6wQZEF2JZRptoL3OpG0wSnKd0uOy4GtTyILodSAToVN/Pe3UTiL6/sznhlbvbt5MMcdaFGuy6cPkecyaPaLocynKdNV085htI3nSarhW9TvPiVFg+nLKp+YlGN7crVVKu+YHfRRttqBNTeImPXH8EMyJjvFARim0wXZZqI7hlGQXIZlUm5t4QTdvSa111iZS3TeXjuMlvyQhCSZCNwRx100Oo+E0wjCK8I0LGtIxIlzaWnD6gXOsN44XLpVeNYVUysVve1tfQGAk+GbLjdU4GIGMmIiM2nd50GIpl/YzpnvtkzjNfpa81jW4SVJrTU7SvQPtIFcKhdwULnIoFiDlOu2uh5mcThsaygqLG/O/wsZTiMS7gBnZgosoJJCjkoPsjyl3ZmDaq2VCgP8AnqJTGptoXYAnymcrO6uMvUUM15Xmm+Tu5WZQQEOZio/4tG9wSDoX20Oux3BsRNLiaLI7IwswNjqD8RofSZmUvEayxuPaAkmbSQUxsZakqTLykD5Sd5EmJVukEtx0kqi2O6n1H6xJfW0lVdjvtPf4/FL4rlZz8cMbRpi53A89pehbcaaE6a6X3PKYiC8uLm2/MTy3D7d6al02bYt8hQte4OYHW3K3npp5zAQaXlF5ZmItOHrpr2t7DyMkTK5qM07yb0mCqxHha+U8DlNmt5GVkwmkSI0vpvbcX929td9pl4ZKZR87EOLZAACCb65jfw6cgfSYUJmzbWOWr0tWsRoDK2aREY5xJouVohCAmmVmLYMxICi4XYMovlF7BRYa32hIWhG0C7zYUOz3ZDVA8C2vqAdTbQXvwmuE6HC4z+6vTCMdVYsB4QBnJzHhuJ6Pp8MMt+34Z8nkzx16/mf8c/iCC5K3tfS+/rFBmuTCcLx03bu7MGSPCQWTc7aS4zu6EXEaCRvfT3CSRDew393xkl1QONJLC6mWY/COgUuBZr2IYNe2+x6iRwBFzfpy9d5i3jbUmrpbUqnLfnp8f6THruWJJ6fAASdrqBmXotyTueAErek/8Df7TJJFy3SQyTHSNKLcreekTEcDf0muGdXSN5IjSRjJlQ0A439LSWRbbn4fpIK0RNyZ7/F58MPHqzdZs3To2ub36bfWSa3DaVrJNvOF80/T9YuvkERsdOsZQixOsPSeXbchNC28DHpr5D5SLqKhJARGAm2EvuzyMkKTcjK4ScrwmaTcjI2ihKbnwLwvDLAiGRCEIElWbDAYl1BVblSbkaAW4gneYAc8o1qML8Lzfi8lwu1zwmU1pUxuSepjgBGZmoBLK1UtYnlb3SoSTiankykuMvF7XXygp1loNybdJFOB5Ha31mQCCB5anrYf1nLKt4zarEVGZQC1wL2HK+/yEMISMxuRttbrz8oVToAbGJGHAW9T1k+C8ZM/DpUZL2NiQNEGouNfZmK1EnRlK7+1YfJfpJUnFgCx9pdLm1rnh7phAnmZJLutZWcM0UwptmX0zdem+0xgN9R75Mjxe/5mRwlLOwW9r318gT9JZxyzlzqSIxXjKiICbYsAEkVgN5ajrxHrpzHTTj75LVkUR5eMkbFjbQcIiZRLOLQanYkcj8tJDNGDJo3sCBMRMI0BpERkxgaX62lNIiOFoQmheEIrQaOKFoQaOEIQulpi5whObshFCE6OBiW1OEITPzFnSykg00HtfQTH/EfT5QhOmXS/BVNh5mFP9+4whOfwXtbQ39V+cKfDy+oihC4pD2h+X9Zc2484oTGTf5Yq7+sm3s+6EJtiID6CNOMIQiA3hCE1WaRgIQgiYgIQmVRaTPs+v0hCFiAjhCEAhCEBmAhCHX4RhCEOT//Z", quantity: 0 ,
    text_box:'ดนตรีสดไพเราะ เหมาะแก่การสังสรรค์ มีทีวีและโปรเจกเตอร์ สำหรับคอบอล อาหารอร่อยถูกปากและเครื่องดื่มราคาถูก นั่งดื่มพูดคุยสนุกสนานาข้ามคืน ยินดีต้อนรับเสมอ'
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
  