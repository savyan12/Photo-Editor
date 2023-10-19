<template>
  <PhotoEditor></PhotoEditor>
  <div class="message w-100 h-100 position-absolute  top-0 start-0 bg-dark" id="message" >
        <img src="./assets/Home.png" alt="Photo"  class="mx-auto" style="width: 40%; margin-top: 8%;" @load="loading">
        <br>
        <br>
        <div class="spinner-border text-light" role="status">
            <span class="visually-hidden">Loading...</span>
        </div>
        <br>
        <p class="fs-2 text-warning">Loading...</p>
    </div>
    <div class="container">
      <footer class="py-1 px-2 bg-dark sh">
      <span>Powered by</span>
      <a  class="link-offset-2 link-underline link-underline-opacity-0" target="_blank" href="https://ssufyan.netlify.app/">
        Sufyan
      </a> <img src="data:image/webp;base64,UklGRpQCAABXRUJQVlA4TIgCAAAvv8QvAV9gJmCSUYEY1Caep5eXNRS0kcI8BvZyjz9UoKBtGyYt+0H+m/8A/H8DyRgEAY3lhBgQbsNeAoTItoU2sRAL1YCDEAdoqAUstA7QgIUa/PMhn88rvI3ovxNEkiQpCgrW7pTee9XXB+an8Zm7K/zHf/zHf/yXaVhaOuKzVvzHf/zHf/x3e9U5I+Y//uM//gsoS3wV/2V1lvgq/uM//uM//otnrV8s//Ef/917/MZX5UeW+Cr+uwKaS9LUxfIf//Ef//FfguUY3/j22KzwH//xH//xXyKj+Ys9xPAf//Hfpd4UX8V/V2JDfFUmY95Vxo4I//Ef//Ef/+VJxu4K/2U/pv+2esXXRaZkiK9K0rzjq/iP/4LKXCmNsDYr/JdlmuKr+I//+O+MmuKr7vnmkrTL2vjwH//xH/9dI7ziq/gv3K2HmLTEEF/Ff/zHf1mgKb6K/3rVXBL+4z/+4z/+y8N0Vx4lWTsi/Md//Md//Md//Md/aDDEV/Ef/138PEvSrjfkPVbKsyRFHiXhP/7jP/67u3jHV/Ef//Ef//Ef/6Wrjjr8x3/8x3/8x3/8x3/8x3/8dxXwVyn8x3/8x3/8d5MXX89F5z/+4z/+4z/+4z/+4z/+478Q1oVT74kR8x//8R//8V/qZF9j2f0W+Y//+I//+C+HcIqmvl0+ccT8x3/8x3/8l02ptbKmvmNu/uM//uM//kvD/JWkEVOvdYv4j//4j//4777vDD0EvdbUP3HEGz4qnf/4j//4j//yJI+SfJek1jyrTX27bDjiIhvebv7jP/7jP/7LgNQ6zQ1Vm/p2qTXifak1df7jP/7jP/7LbdQ6ug21/k+ot/tD4T/+4z/+47+swgw=" alt="" class="imgSh" width="40">
      &copy;  
    </footer>
    </div>
    
</template>
<script>
import PhotoEditor from "@/components/PhotoEditir.vue";
export default {
  name: 'App',
  components: {
    PhotoEditor
  },
  methods: {
    loading(){
            let message = document.getElementById("message");
            window.onload = setTimeout(() => {
            message.style.display = "none";
            }, 1000);
            
        },
  },
}
</script>
<style lang="css">
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #ffff;
  margin-top: 60px;
}
.sh {
  margin-top: 90px;
  box-shadow: 10px 8px 20px rgba(0, 0, 0, 0.151);
}
.imgSh {
  margin: 0 5px;
  width: 40px;
  height: 40px;
  border-radius: 50%;
}
</style>
