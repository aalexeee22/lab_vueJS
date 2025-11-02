<template>
<form @submit.prevent="addProduct">    
       <label for="name">Nume Produs:</label>
      <input type="text" id="name" v-model="product.name" placeholder="Nume Produs" />
       <p v-if="nameError">{{ nameError }}</p>
      <label for="price">Preț Produs:</label>
      <input type="number" id="price" v-model="product.price" placeholder="Preț Produs" />  
    <button type="submit" >{{ isEditing?"Salveaza":"Adauga" }}</button>
  </form>
</template>
<script>
export default
{
  props: {
    isEditing: {
      type: Boolean,
      default: false
    },
  },
  data(){
  return{
    product:{
      name: "",
      price: null
    }
  }
},
  
  methods:  
  {
    addProduct(){
      this.$emit('add-product', { ...this.product });
      this.product.name = "";
      this.product.price = null;
  

    },

    // submit() 
    // {
    // // Logica pentru trimiterea formularului
    //   console.log('Nume:', this.name);
    //   console.log('Price:', this.price);
    // },
    
  },
  watch: {
    'produc.name'(newVal) {
      if (newVal.trim() === '') {
        this.nameError = 'Numele produsului nu poate fi gol.';
      } else {
        this.nameError = '';
      }
    },
  }
};
</script>
<style></style>