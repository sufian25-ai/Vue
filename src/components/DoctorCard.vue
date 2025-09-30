<script setup lang="ts">

const props = defineProps({
  doctor: {
    type: Object,
    required: true
  }
})

const emit = defineEmits(['book'])

function bookDoctor() {
  emit('book', props.doctor)
}

</script>
<template>
  <div class="card h-100">
    <img :src="doctor.photo" :alt="doctor.name" class="card-img-top" />
    <div class="card-body">
      <h5 class="card-title">{{ doctor.name }}</h5>
      <p class="card-text">Specialty: {{ doctor.specialty }}</p>
      <p class="card-text">Consultation Fee: ${{ doctor.fee }}</p>
      <button class="btn btn-primary" @click="bookDoctor">Book Appointment</button>
    </div>
  </div>
</template>

<style scoped>
.card {
  border: none;
  border-radius: 15px;
  box-shadow: 0 4px 15px rgba(0, 0, 0, 0.1);
  transition: all 0.3s ease;
  overflow: hidden;
  background: linear-gradient(135deg, #ffffff 0%, #f8f9fa 100%);
}

.card:hover {
  transform: translateY(-5px);
  box-shadow: 0 8px 25px rgba(0, 0, 0, 0.15);
}

.card-img-top {
  width: 150px;
  height: 150px;
  object-fit: cover;
  border-radius: 50%;
  margin: 20px auto 0;
  display: block;
  transition: transform 0.3s ease;
  border: 3px solid #fff;
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
}

.card:hover .card-img-top {
  transform: scale(1.1);
}

.card-body {
  padding: 20px;
  text-align: center;
}

.card-title {
  font-size: 1.5rem;
  font-weight: 700;
  color: #2c3e50;
  margin-bottom: 10px;
}

.card-text {
  font-size: 1rem;
  color: #6c757d;
  margin-bottom: 8px;
}

.card-text:last-of-type {
  font-weight: 600;
  color: #28a745;
  font-size: 1.1rem;
}

.btn-primary {
  background: linear-gradient(135deg, #007bff 0%, #0056b3 100%);
  border: none;
  border-radius: 25px;
  padding: 10px 20px;
  font-weight: 600;
  text-transform: uppercase;
  letter-spacing: 0.5px;
  transition: all 0.3s ease;
  box-shadow: 0 4px 15px rgba(0, 123, 255, 0.3);
}

.btn-primary:hover {
  background: linear-gradient(135deg, #0056b3 0%, #004085 100%);
  transform: translateY(-2px);
  box-shadow: 0 6px 20px rgba(0, 123, 255, 0.4);
}

.btn-primary:active {
  transform: translateY(0);
  box-shadow: 0 2px 10px rgba(0, 123, 255, 0.3);
}

@media (max-width: 768px) {
  .card-body {
    padding: 15px;
  }

  .card-title {
    font-size: 1.3rem;
  }

  .card-img-top {
    width: 120px;
    height: 120px;
    margin-top: 15px;
  }
}
</style>
