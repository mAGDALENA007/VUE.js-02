<template>
    <div id="app1">
    <div class="contain">
        <section class="main"> 
          <h2>Zalecenia lekarsie - generator</h2>
          <h3>Wybierz i wpisz zalecenia dla nowego pacjęta:</h3>
        </section>
        <div class="new">
          <form @submit.prevent="addReq">
            <table>
              <tbody>
  
                <!-- Choose Medicament -->
                <tr>
                  <td> 
                    1. Lekarstwo: <select v-model="newMed" required>
                    <option disabled value="">Wybierz lek</option>
                    <option>Witamina C</option>
                    <option>Witamina D</option>
                    <option>Apap</option>
                    <option>Polopiryna</option>
                    </select> 
                  </td>
                </tr>
  
                <!-- Choose Time -->
                <tr>
                  <td>2. Zalecana pora podania: <select v-model="newTime" required>
                    <option disabled value="">Godzina podania leku</option>
                    <option>8:00 - rano</option>
                    <option>15:00 - po południu</option>
                    <option>22:00 - wieczorem</option>
                    </select>
                  </td>
                </tr>
  
                <!-- Choose Calendar -->
                <tr>
                  <td>3. Data i godzina rozpoczęcia leczenia:
                      <div id="app"></div>    
                  </td>
                </tr>
  
                <!-- Choose Amount of Medicament-->
                <tr>
                  <td>4. Zalecana ilość leku: <select v-model="newAmount" required>
                    <option disabled value="">Ilość leku</option>
                    <option>1 tabletka</option>
                    <option>2 tabletki</option>
                    <option>3 tabletki</option>
                    </select>
                  </td>
                </tr>
  
                <!-- Choose Hospital Department-->
                <tr>
                  <td>5. Odział: <select v-model="newDepartment" required>
                    <option disabled value="">Oddział szpitalny</option>
                    <option>Chirurgia</option>
                    <option>Ortopedia</option>
                    <option>Kardiologia</option>
                    </select>
                  </td>
                </tr>
  
                <!-- Select a Patient-->
                <tr>
                  <td>6. Imię: <input v-model="newName" placeholder="Imię" required/></td>
                </tr>
                <tr>
                  <td>7. Nazwisko: <input v-model="newSurname" placeholder="Nazwisko" required/></td>
                </tr>
                <tr>
                  <td>8. PESEL: <input v-model="newPesel" placeholder="PESEL" required/></td>
                </tr>
  
                <!-- The End Of Medical Recommendations -->
                <tr>
                  <td><h3>Wystaw zalecenia: <button type="submit">DODAJ NOWEGO PACJĘTA</button></h3></td>
                </tr>
          </form>
          </tbody>
        </table>
        </div> <!--/ .new-->
  
        <!-- Registered Recommendations -->
        <div v-for="(post, i) in filteredByLabel" class="post">
          <h3>Pacjęt:</h3>
          <p><strong> {{ post.surname }} </strong> {{ post.name }} , PESEL:{{ post.pesel }} </p>
          <p><bold>{{ post.label }}</bold>, godzina: {{ post.time }}, ilość: {{ post.amount }} </p>
          <p><small>Pacjęt przebywa na oddziale: {{ post.department }} </small></p>
        </div>
    </div> <!--/ .contain-->
  </div> <!--/ .app1-->
</template>

<script>
   // Add Medical recommendations to array and display on screen
new Vue({
  el: '#app1',
  data() {
    return {
      selected: '',
      posts: [
        {
          name: 'Tomasz',
          surname: 'Kowalski',
          pesel: '123456',
          time: '8:00',
          amount: '1 tabletka',
          department: 'Chirurgia',
          label: 'Apap'
        },
        {
          name: 'Anna',
          surname: 'Nowak',
          pesel: '234567',
          time: '15:00',
          amount: '2 tableki',
          department: 'Ortopedia',
          label: 'Polopiryna'
        },
        {
          name: 'Jan',
          surname: 'Woźniak',
          pesel: '345678',
          time: '22:00',
          amount: '3 tabletki',
          department: 'Kardiologia',
          label: 'Witamina C'
        }
      ],
      newName: '',
      newSurname: '',
      newPesel: '',
      newTime: '',
      newAmount: '',
      newDepartment: '',
      newMed: ''
    }
  },
  methods: {
    addReq() {
      let addedPost = new Object({
        name: this.newName,
        surname: this.newSurname,
        pesel: this.newPesel,
        time: this.newTime,
        amount: this.newAmount,
        department: this.newDepartment,
        label: this.newMed
      });
      this.posts.push(addedPost)
      this.newName = '';
      this.newSurname = '';
      this.newPesel = '';
      this.newTime = '';
      this.newAmount = '';
      this.newDepartment = '';
      this.newMed = '';
    }
  },
  computed: {
    filteredByLabel() {
      let filter = new RegExp(this.selected, 'i')
      return this.posts.filter(el => el.label.match(filter))
    }
  }
})

</script> 
 
<template>
</template>

<style>
</style>
