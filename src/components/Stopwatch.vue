<template>
  <div class="wrapper">
    <div class="content">
    <div class="timer">
        {{timer}}
        </div>
    <div class="btns">
      <button v-if='state === "running"' @click="$emit('pause')" class="btn btn--pause" type="button"></button>
      <button v-else @click="$emit('start')" class="btn btn--triangle" type="button"></button>
      <button v-if='state === "stopped"' class="btn btn--square" type="button"></button>
      <button v-else @click="$emit('stop')" class="btn btn--white-square" type="button"></button>
      
    </div></div>
  </div>
</template>

<script>
export default {
  props: ['timer', 'state']
}
</script>


<style scoped>
.wrapper {
    background-color: #696969;
    display: flex;
    position: fixed;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
}

.content {
    display: flex;
    align-items: center;
    flex-direction: column;
        width: 225px;
    height: 120px;
}

.timer {
  margin-top: 20px;
  text-align: center;
       width: 100%;
       height: 50%;
    border-bottom: 1px solid #9E9E9E;
     color: #9E9E9E;
     font-size: 22px;
line-height: 21px;
}

.btns {
  margin-top: 20px;
  height: 50%;
}

.btn--triangle {
  background-image: url(../assets/img/triangle.svg);
  width: 17px;
height: 20px;
}

.btn--pause {
    background-image: url(../assets/img/pause.svg);
  width: 10px;
height: 20px;
}

.btn--square {
   background-image: url(../assets/img/square.svg);
  width: 17px;
height: 20px;
margin-left: 48px;
}

.btn--white-square {
    background-image: url(../assets/img/white-square.svg);
  width: 17px;
height: 20px;
margin-left: 48px;
}

</style>