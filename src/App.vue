<script setup>
  import { ref } from 'vue'
  const isActive = ref(0)
  const images = [
    {
      thumb: "https://images.unsplash.com/photo-1682685797769-481b48222adf?ixlib=rb-4.0.3&ixid=M3wxMjA3fDF8MHxlZGl0b3JpYWwtZmVlZHwxfHx8ZW58MHx8fHx8&auto=format&fit=crop&w=300&q=60",
      title: 'First slide label',
      content: 'Some representative placeholder content for the first slide.'
    },
    {
      thumb: "https://images.unsplash.com/photo-1682695794816-7b9da18ed470?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1yZWxhdGVkfDZ8fHxlbnwwfHx8fHw%3D&auto=format&fit=crop&w=300&q=60",
      title: 'Second slide label',
      content: 'Some representative placeholder content for the first slide.'
    },
    {
      thumb: "https://images.unsplash.com/photo-1682685797661-9e0c87f59c60?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1yZWxhdGVkfDE4fHx8ZW58MHx8fHx8&auto=format&fit=crop&w=300&q=60",
      title: 'Third slide label',
      content: 'Some representative placeholder content for the first slide.'
    },
    {
      thumb: "https://plus.unsplash.com/premium_photo-1666963323736-5ee1c16ef19d?ixlib=rb-4.0.3&ixid=M3wxMjA3fDB8MHxwaG90by1yZWxhdGVkfDE2fHx8ZW58MHx8fHx8&auto=format&fit=crop&w=300&q=60",
      title: 'Fourth slide label',
      content: 'Some representative placeholder content for the first slide.'
    }
  ]

  const prev = () => {
    isActive.value <= 0 ? isActive.value = ( images.length - 1 ) : isActive.value--
  }

  const next = () => {
    isActive.value >= ( images.length - 1 ) ? isActive.value = 0 : isActive.value++
  }

  const indicators = (index) => {    
    isActive.value = index    
  }

</script>

<template>
  <div class="container">
    <div class="row">
      <div class="col-md-8 offset-md-2">
        <div id="carouselExampleCaptions" class="carousel slide" data-bs-ride="false">
          <div class="carousel-indicators">
            <button @click="indicators(index)" type="button" data-bs-target="#indicators" v-for="(image, index) in images" :key="index" :class="index == isActive ? 'active': ''"></button>
          </div>
          <div class="carousel-inner">
            <div class="carousel-item" v-for="(image, index) in images" :key="index" :class="index == isActive ? 'active': ''">
              <img :src="image.thumb" class="d-block w-100 h-571" :alt="image.title">
              <div class="carousel-caption d-none d-md-block">
                <h5>{{ image.title }}</h5>
                <p>{{ image.content }}</p>
              </div>
            </div>
          </div>
          <button @click="prev" class="carousel-control-prev" type="button" data-bs-target="#carouselExampleCaptions" data-bs-slide="prev">
            <span class="carousel-control-prev-icon" aria-hidden="true"></span>
            <span class="visually-hidden">Previous</span>
          </button>
          <button @click="next" class="carousel-control-next" type="button" data-bs-target="#carouselExampleCaptions" data-bs-slide="next">
            <span class="carousel-control-next-icon" aria-hidden="true"></span>
            <span class="visually-hidden">Next</span>
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped>
  .h-571 {
    height: 571px;
  }
</style>
