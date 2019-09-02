<template>
  <div>
    <b-card title="Sign Up" style="max-width: 20rem;">
    <b-form @submit="onSubmit" @reset="onReset" v-if="show">
      <b-form-group
        id="input-group-1"
        label="Email address:"
        label-for="input-1"
        description="We'll never share your email with anyone else."
      >
        <b-form-input
          id="input-1"
          v-model="form.email"
          type="email"
          required
          placeholder="Enter email"
        ></b-form-input>
      </b-form-group>

      <b-form-group id="input-group-2" label="Password:" label-for="input-2">
        <b-form-input
          id="input-2"
          v-model="form.encrypted_password"
          required
          placeholder="Enter password"
        ></b-form-input>
      </b-form-group>

      <b-form-group id="input-group-3" label="Username:" label-for="input-3">
        <b-form-input
          id="input-3"
          v-model="form.username"
          required
          placeholder="Enter username"
        ></b-form-input>
      </b-form-group>

      <b-form-group id="input-group-4" label="Phone Number:" label-for="input-4">
        <b-form-input
          id="input-4"
          v-model="form.phone"
          type="number"
          required
          placeholder="Enter phone number"
        ></b-form-input>
      </b-form-group>

      <b-form-group id="input-group-5" label="Address:" label-for="input-5">
        <b-form-input
          id="input-5"
          v-model="form.address"
          required
          placeholder="Enter address"
        ></b-form-input>
      </b-form-group>

      <b-form-group id="input-group-6" label="City:" label-for="input-6">
        <b-form-input
          id="input-6"
          v-model="form.city"
          required
          placeholder="Enter city"
        ></b-form-input>
      </b-form-group>

      <b-form-group id="input-group-7" label="Country:" label-for="input-7">
        <b-form-input
          id="input-8"
          v-model="form.country"
          required
          placeholder="Enter country"
        ></b-form-input>
      </b-form-group>

      <b-form-group id="input-group-8" label="Name:" label-for="input-8">
        <b-form-input
          id="input-8"
          v-model="form.name"
          required
          placeholder="Enter name"
        ></b-form-input>
      </b-form-group>

      <b-form-group id="input-group-9" label="Postcode:" label-for="input-9">
        <b-form-input
          id="input-9"
          v-model="form.postcode"
          type="number"
          required
          placeholder="Enter postcode"
        ></b-form-input>
      </b-form-group>

      <b-button type="submit" variant="primary">Submit</b-button>
      <b-button type="reset" variant="danger">Reset</b-button>
    </b-form>
    <b-card class="mt-3" header="Form Data Result">
      <pre class="m-0">{{ form }}</pre>
    </b-card>
    </b-card>
  </div>
</template>

<script>
import axios from 'axios'

  export default {
    data() {
      return {
        form: {
          username: '',
          email: '',
          encrypted_password: '',
          phone: '',
          address: '',
          city: '',
          country: '',
          name: '',
          postcode: ''
        },
        show: true
      }
    },
    methods: {
      onSubmit(evt) {
        evt.preventDefault()
        alert(JSON.stringify(this.form))
        const submitNewUser = {
          username: this.form.username,
          email: this.form.email,
          encrypted_password: this.form.encrypted_password,
          phone: this.form.phone,
          address: this.form.address,
          city: this.form.city,
          name: this.form.name,
          postcode: this.form.postcode
        }
        const { username, email, encrypted_password, phone, address, city, name, postcode} = submitNewUser
      },
      onReset(evt) {
        evt.preventDefault()
        // Reset our form values
        this.form.username = ''
        this.form.email = ''
        this.form.encrypted_password = ''
        this.form.phone = ''
        this.form.address = ''
        this.form.city = ''
        this.form.country = ''
        this.form.name = ''
        this.form.postcode = ''
        // Trick to reset/clear native browser form validation state
        this.show = false
        this.$nextTick(() => {
          this.show = true
        })
      }
    }
  }
</script>