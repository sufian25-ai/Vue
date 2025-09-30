<script setup lang="ts">
import { ref } from 'vue'
import BookingForm from './BookingForm.vue'
import DoctorCard from './DoctorCard.vue'


const selectedDoctor = ref('')
const doctors = ([
  {
    id: 1,
    name: 'Dr. Raman',
    specialty: 'Cardiology',
    fee: 500,
    photo: 'images/image.jpg'
  },
  {
    id: 2,
    name: 'Dr. Smith',
    specialty: 'Dermatology',
    fee: 300,
    photo: 'images/smith.jpg'
  },
  {
    id: 3,
    name: 'Dr. Lee',
    specialty: 'Pediatrics',
    fee: 400,
    photo: 'images/lee.jpg'
  }
])

function handleBook(doctor)
{
  selectedDoctor.value = doctor.name

}

function onBooked(payload)
{
  alert('Booking confirmed for ' + payload.name + ' with ' + payload.doctor + ' on ' + payload.date)
}


</script>
<template>
  <div>
  <h1>DOctor deatils</h1>
  <div class="mb-4">
   <BookingForm :prefillDoctor="selectedDoctor" @booked="onBooked" ref="apptForm" />
    </div>

    <hr />
    <h3>Our specialist</h3>
    <div class="row">
      <div class="col-md-4 mb-3" v-for="doc in doctors" :key="doc.id">
        <DoctorCard :doctor="doc" @book="handleBook" />
      </div>
    </div>
</div>

</template>
