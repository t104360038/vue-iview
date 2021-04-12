<template>
  <Carousel autoplay v-model="value2" loop>
    <CarouselItem>
      <div class="demo-carousel">1</div>
    </CarouselItem>
    <CarouselItem>
      <div class="demo-carouse2">2</div>
    </CarouselItem>
    <CarouselItem>
      <div class="demo-carouse3">3</div>
    </CarouselItem>
    <CarouselItem>
      <div class="demo-carouse4">4</div>
    </CarouselItem>
  </Carousel>
</template>
<script>
export default {
  data() {
    return {
      value2: 0,
    };
  },
};
</script>
<style scoped>
.demo-carousel {
  background-image: url("https://static.accupass.com/a_dvert/2009220933081207256010.jpg");
  background-size: Cover;
  height: 76vh;
  /* width: 60vw; */
}
.demo-carouse2 {
  background-image: url("https://static.accupass.com/a_dvert/2009220919199467679870.jpg");
  background-size: Cover;
  height: 76vh;
  /* width: 60vw; */
}
.demo-carouse3 {
  background-image: url("https://static.accupass.com/eventbanner/2004220628301591161702.jpg");
  background-size: Cover;
  height: 76vh;
  /* width: 60vw; */
}
.demo-carouse4 {
  background-image: url("https://www.seinsights.asia/sites/default/files/imagecache/event_list_v3/upload/field/images/field_insert/event/2021_ya_tai_she_hui_chuang_xin_gao_feng_hui_.jpg");
  background-size: Cover;
  height: 76vh;
  /* width: 60vw; */
}
</style>
