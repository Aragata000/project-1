<template>
  <div class="home-view">
    <h1>Hola</h1> 
    <create-car-form @submit="handleAddCar"/>
    <div class="home-view-cars-container">
      <car-card v-for="car in cars" :key="car.matricula" :car="car"/> 
        
    </div> 
  </div>
</template>

<script>
  import CreateCarForm from "@/components/CreateCarForm.vue"
  import { ref } from '@vue/reactivity'
import CarCard from '@/components/CarCard.vue'
  export default{
    components: {
      CreateCarForm,
        CarCard
    },
    setup() {
      const cars = ref([])
      const handleAddCar = (car) => {
        cars.value.push(car)
      }
      return {
        cars,
        handleAddCar
      }
    }
  }
</script>

<style scoped>
.home-view-cars-container {
  display: grid;
  grid-template-columns: 1fr 1fr 1fr;
  gap: 10px;
}
</style>