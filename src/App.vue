<script>
import userProfile from './components/userProfile.vue'
export default {

  components: {
    userProfile,
  },

  data() {
    return {
      name: '',
      email: 'mehdiraza@folio3.com',
      age: 25,
      ageMessage: '',
      hobby: "",
      hobbies: []
    }
  },
  mounted() {
    this.name = "Imran"
    this.age = 40
  },
  computed: {
    birthYear() {
      const currentYear = new Date().getFullYear();
      return currentYear - this.age;
    },
  },
  watch: {
    'age'(newAge) {
      if (newAge > 50) {
        this.ageMessage = 'Age too big';
      } else {
        this.ageMessage = '';
      }
    },
  },

  methods: {
    submitForm(e) {
      e.preventDefault()
      const nameInput = this.$refs.nameInput; // Access the form
      const ageInput = this.$refs.ageInput; // Access the name input element
      const emailInput = this.$refs.emailInput; // Access the email input element

      console.log("Name from ref: " + nameInput.value);
      console.log("Email from ref: " + emailInput.value);
      console.log("Age from ref: " + ageInput.value);

    },

    addHobby() {
      this.hobbies.push({ name: this.hobby })
    },
  }

}
</script>

<template>
  <head>
    <title>User Form</title>
  </head>

  <body>
    <form>
      <label for="name">Name:</label>
      <input type="text" id="name" name="name" v-model="name" ref="nameInput" required><br><br>

      <label for="age">Age:</label>
      <input type="number" id="age" name="age" v-model="age" ref="ageInput" required><br><br>

      <label for="email">Email:</label>
      <input type="email" id="email" name="email" v-model="email" ref="emailInput" required><br><br>

      <input type="submit" value="Submit" @click="submitForm">
    </form>
    <div>
      <userProfile :name="name" :email="email" :age="age" :birthYear="birthYear"></userProfile>
      <p><strong>Message:</strong> {{ ageMessage }}</p>
    </div>


    <div>

    <h1>Hobbies List</h1>
    <div>
      <input type="text" v-model="hobby" @keyup.enter="addHobby">
      <button @click="addHobby">Add</button>
    </div>
    <div>
      <ul>
        <li v-for="(hobby, index) in hobbies" :key="index">
          <div>
            <div>
              <p><strong>Hobby:</strong> {{ hobby.name }}</p>
            </div>
          </div>

        </li>
      </ul>
    </div>

  </div>


  </body>
</template>

<style scoped>
  form {
    background-color: #000000;
    padding: 20px;
    border-radius: 10px;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.2);
    margin: 20px;
  }

  label {
    display: block;
    font-weight: bold;
    margin-bottom: 5px;
  }

  input {
    width: 100%;
    padding: 10px;
    margin-bottom: 15px;
    border: 1px solid #ccc;
    border-radius: 5px;
  }

  input[type="submit"] {
    background-color: #007BFF;
    color: #fff;
    border: none;
    border-radius: 5px;
    padding: 10px 20px;
    cursor: pointer;
  }

  input[type="submit"]:hover {
    background-color: #0056b3;
  }
</style>

