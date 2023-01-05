<template>
  <div class="car-card">
    <div class="car-card-matricula">
        {{ car.matricula }}
    </div>
    <div class="car-card-marca">
        {{ car.marca }}
    </div>
  </div>
</template>

<script>
export default {
    props: {
        car: {
            type: Object,
            required: true
        }
    },
    setup(props) {
        return {
            ...props
        }
    }      
}
</script>

<style scoped>
.car-card {
    background: red;
}
</style>