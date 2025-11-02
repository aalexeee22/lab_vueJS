<!-- <template>
  <div>
    <h1>{{ title }}</h1>
    <p>{{ description }}</p>
    <p>{{ concatTitluSiHeader }}</p>

    <input v-model="title" placeholder="Schimba titlul aici" />
    <input v-model="description" placeholder="Schimba descrierea aici" />
    <button @click="schimbaTextul">Schimba textul</button>
    <button @click="increase">Click count: {{ numberOfClicks }}</button>
    <ButtonWithPopup 
      buttonText="Arată popup" 
      popupMessage="Acesta este un mesaj din popup!" 
      />

  </div>
<ButtonWithPopup 
      buttonText="Arată popup 2" 
      popupMessage="Acesta este un alt mesaj din popup!" 
      />
</template>

<script>
import ButtonWithPopup from './components/ButtonWithPopup.vue';
export default{
  components:
  {
    ButtonWithPopup
  },
data(){
  return{
    title:"My first vue app",
    description:"This is my first vue app",
    numberOfClicks: 0
  };
},
//props
//getters
//mutations
//actions
methods:
{
  schimbaTextul()
  {
    this.title="Textul a fost schimbat!";
    this.description="Descrierea a fost schimbata!";
  },
  increase()
  {
    this.numberOfClicks++;
    //varianta 1
    // if(this.numberOfClicks > 10)
    // {
    //   alert("Ai atins 10 click-uri!");
    //   this.numberOfClicks = 0;
    // }
    //varianta 2
    
  }
},
computed:
{
  concatTitluSiHeader(){
    return this.title + " - " + this.description;
  }

},
watch:
{
  numberOfClicks(newValue)
  {
    if(newValue > 10)
    {
      alert("Ai atins 10 click-uri!");
      this.numberOfClicks = 0;
    }
  }
},
//lifecycle hooks
mounted()
{
  console.log("Componenta a fost montata!");
}
};
</script>

<style >
/* Stiluri CSS pentru componenta App.vue */
h1 {
  color: #42b983;
}
p {
  font-size: 16px;
}
button {
  margin: 5px;
  padding: 10px;
  background-color: #35495e;
  color: white;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}
button:hover {
  background-color: #42b983;
}
input {
  margin: 5px;
  padding: 8px;
  border: 1px solid #ccc;
  border-radius: 4px;
}

</style> -->
<!-- 
//from cu validare
<template>
  <form @submit.prevent="validateForm">
    <label for="name">Nume:</label>
    <input type="text" placeholder="Nume" v-model="name" />
     <p v-if="nameError">{{ nameError }}</p>
    <label for="email">Email:</label>
    <input type="text" placeholder="Email" v-model="email" />
    <p v-if="errorMail">{{ errorMail }}</p>
    <button type="submit">Trimite</button>
  </form>
</template>
<script>
export default
{
  data()
  {
    return{
      name: "",
      email: "",
      errorMail: '',
      nameError: ''
    };
  },

  methods: 
  {
    submit() 
    {
    // Logica pentru trimiterea formularului
      console.log('Nume:', this.name);
      console.log('Email:', this.email);
    },
    validateForm(){
      this.errorMail='';
      this.nameError='';
      if(this.name === "" || this.email === "")
      {
        this.nameError='Toate câmpurile sunt obligatorii.';
      }
      // Simplu regex pentru validarea email-ului
      const emailPattern = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
      if(!emailPattern.test(this.email))
      {
        this.errorMail='Te rog introdu un email valid.';
      }
      this.submit();
    }
  },
};
</script>
<style></style> -->

<template>
  <div>
    <input v-model="searchQuery" placeholder="Caută un produs..." />
    <ProductList :products="filteredProducts" />
    
  </div>
</template>

<script>
import ProductList from './components/ProductList.vue';

export default {
  components: { ProductList },
  data() {
    return {
      searchQuery: '',
      products: [
        { id: 1, name: 'Laptop', price: 2500 },
        { id: 2, name: 'Telefon', price: 1500 },
        { id: 3, name: 'Tableta', price: 800 },
        { id: 4, name: 'Căști', price: 200 },
        { id: 5, name: 'Monitor', price: 1200 },
      ],
    };
  },
  computed: {
    filteredProducts() {
      return this.products.filter((p) =>
        p.name.toLowerCase().includes(this.searchQuery.toLowerCase())
      );
    },
  },
};
</script>
<style>
input {
  width: 100%;
  padding: 12px 20px;
  margin-bottom: 20px;
  box-sizing: border-box;
  border: 2px solid #ccc;
  border-radius: 4px;
  font-size: 16px;
}
h1 {
  font-family: 'Poppins', sans-serif;
  color: #333;
  text-align: center;
  margin-bottom: 20px;
}

ul {
  list-style: none;
  padding: 0;
}

li {
  background: #f8f9fa;
  margin-bottom: 10px;
  padding: 12px 16px;
  border-radius: 10px;
  border: 1px solid #e2e2e2;
  transition: all 0.2s ease;
}

li:hover {
  transform: translateY(-2px);
  background-color: #fff;
  box-shadow: 0 3px 6px rgba(0, 0, 0, 0.1);
}
</style>