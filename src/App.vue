<script setup lang="ts">
import { computed, ref } from 'vue'
import TodoList from './components/todoList.vue'
const patientName = ref('')

const firstName = ref('Mahbub')
const lastName = ref('Sufian')

const fullName = computed(()=> {
  return firstName.value + " " + lastName.value
})

const price = ref(1000)
const discount = ref(10)

const discountPrice = computed(()=> {
  return price.value - (price.value * discount.value / 100)
})

const doctor = {
  name: 'Dr. Raman',
  photo: 'images/image.jpg'
}

const visits = ref(0)
const bookd = ref(false)
const doctors = [
  {
    name: 'Dr. Raman',
    specialty: 'Cardiology',
    photo: 'images/image.jpg'
  },
  {
    name: 'Dr. Smith',
    specialty: 'Dermatology',
    photo: 'images/smith.jpg'
  },
  {
    name: 'Dr. Lee',
    specialty: 'Pediatrics',
    photo: 'images/lee.jpg'
  }
]

</script>

<template>

  <div class="app-container">
    <header class="header">
      <h1>Medical Appointment System</h1>
    </header>

    <section class="patient-section">
      <div class="doctor-info">
        <img :src="doctor.photo" :alt="doctor.name" class="doctor-photo" />
        <h2>{{ doctor.name }}</h2>
      </div>

      <div class="patient-form">
        <label for="patientName" class="form-label">Patient Name</label>
        <input
          id="patientName"
          v-model="patientName"
          placeholder="Enter your name"
          class="form-input"
        />
        <p v-if="patientName" class="welcome-message">Welcome, {{ patientName }}!</p>
      </div>

      <div class="visit-counter">
        <p class="visit-text">Total Visits: <span class="visit-count">{{ visits }}</span></p>
        <button @click="visits++" class="btn btn-primary">Add Visit</button>
      </div>

      <div class="booking-section">
        <button @click="bookd = true" class="btn btn-success" :disabled="bookd">Confirm Booking</button>
        <p :class="['booking-status', { 'success': bookd, 'error': !bookd }]">
          {{ bookd ? 'Booking Successful' : 'No Booking Available' }}
        </p>
      </div>
    </section>

    <section class="doctors-section">
      <h2>Available Doctors</h2>
      <div class="doctors-grid">
        <div v-for="doc in doctors" :key="doc.name" class="doctor-card">
          <img :src="doc.photo" :alt="doc.name" class="doctor-card-photo" />
          <h3>{{ doc.name }}</h3>
          <p>{{ doc.specialty }}</p>
        </div>
      </div>
    </section>
  </div>
  <br />
  <p>First: {{ firstName }}</p>
  <p>Last: {{ lastName }}</p>
  <p>Full Name: {{ fullName }}</p>
  <br />
  <p>Price: {{ price }}</p>
  <p>discount: {{ discount }}</p>
  <p>Discount Price: {{ discountPrice }}</p>

<TodoList />
</template>

<style scoped>
.app-container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 20px;
  font-family: 'Segoe UI', Tahoma, Geneva, Verdana, sans-serif;
  background-color: #f8f9fa;
  min-height: 100vh;
}

.header {
  text-align: center;
  margin-bottom: 30px;
}

.header h1 {
  color: #2c3e50;
  font-size: 2.5rem;
  margin: 0;
}

.patient-section {
  background: white;
  border-radius: 10px;
  padding: 30px;
  margin-bottom: 30px;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
}

.doctor-info {
  text-align: center;
  margin-bottom: 30px;
}

.doctor-photo {
  width: 120px;
  height: 120px;
  border-radius: 50%;
  object-fit: cover;
  border: 4px solid #3498db;
  margin-bottom: 10px;
}

.doctor-info h2 {
  color: #2c3e50;
  margin: 0;
}

.patient-form {
  margin-bottom: 30px;
}

.form-label {
  display: block;
  margin-bottom: 8px;
  font-weight: 600;
  color: #34495e;
}

.form-input {
  width: 100%;
  padding: 12px;
  border: 2px solid #bdc3c7;
  border-radius: 5px;
  font-size: 16px;
  transition: border-color 0.3s;
}

.form-input:focus {
  outline: none;
  border-color: #3498db;
}

.welcome-message {
  margin-top: 10px;
  color: #27ae60;
  font-weight: 500;
}

.visit-counter {
  margin-bottom: 30px;
  text-align: center;
}

.visit-text {
  font-size: 18px;
  margin-bottom: 15px;
  color: #34495e;
}

.visit-count {
  font-weight: bold;
  color: #e74c3c;
}

.booking-section {
  text-align: center;
}

.booking-status {
  margin-top: 15px;
  font-weight: 500;
  padding: 10px;
  border-radius: 5px;
}

.booking-status.success {
  background-color: #d4edda;
  color: #155724;
  border: 1px solid #c3e6cb;
}

.booking-status.error {
  background-color: #f8d7da;
  color: #721c24;
  border: 1px solid #f5c6cb;
}

.btn {
  padding: 12px 24px;
  border: none;
  border-radius: 5px;
  font-size: 16px;
  cursor: pointer;
  transition: background-color 0.3s, transform 0.1s;
  margin: 0 5px;
}

.btn:hover {
  transform: translateY(-2px);
}

.btn:disabled {
  opacity: 0.6;
  cursor: not-allowed;
  transform: none;
}

.btn-primary {
  background-color: #3498db;
  color: white;
}

.btn-primary:hover:not(:disabled) {
  background-color: #2980b9;
}

.btn-success {
  background-color: #27ae60;
  color: white;
}

.btn-success:hover:not(:disabled) {
  background-color: #229954;
}

.doctors-section {
  background: white;
  border-radius: 10px;
  padding: 30px;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
}

.doctors-section h2 {
  text-align: center;
  color: #2c3e50;
  margin-bottom: 30px;
}

.doctors-grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 20px;
}

.doctor-card {
  background: #f8f9fa;
  border-radius: 10px;
  padding: 20px;
  text-align: center;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  transition: transform 0.3s, box-shadow 0.3s;
}

.doctor-card:hover {
  transform: translateY(-5px);
  box-shadow: 0 4px 8px rgba(0, 0, 0, 0.15);
}

.doctor-card-photo {
  width: 100px;
  height: 100px;
  border-radius: 50%;
  object-fit: cover;
  margin-bottom: 15px;
  border: 3px solid #3498db;
}

.doctor-card h3 {
  color: #2c3e50;
  margin: 0 0 10px 0;
}

.doctor-card p {
  color: #7f8c8d;
  margin: 0;
}

@media (max-width: 768px) {
  .app-container {
    padding: 10px;
  }

  .patient-section,
  .doctors-section {
    padding: 20px;
  }

  .header h1 {
    font-size: 2rem;
  }

  .doctors-grid {
    grid-template-columns: 1fr;
  }
}
</style>
