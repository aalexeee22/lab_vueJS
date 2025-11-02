<template>
  <div>
    <reusable-form @add-product="addProduct"></reusable-form>
    <h1>Lista de Produse</h1>
    <MyButton buttonName="Add" @functionName="addItem" ></MyButton>
    

    <ul>
      <li v-for="product in localProducts" :key="product.id">
        {{product.id}} - {{ product.name }} - {{ product.price }} RON
        <MyButton buttonName="Delete" @functionName="deleteItem(product.id)"></MyButton>
        <MyButton buttonName="Edit" @functionName="editItem(product)" ></MyButton>
        <!-- <Button buttonName="Edit" ></Button> -->
      </li>
      
    </ul>
  </div>
</template>

<script>
import MyButton from './Button.vue';
import ReusableForm from './ReusableForm.vue';

export default {
  components: { MyButton, ReusableForm},
  name: "ProductList",
  props: {
    products: {
      type: Array,
      required: true
    }
  },
  data() {
    return {
      localProducts: [...this.products]
    };
  },
  methods: {  
    deleteItem(id){
      console.log("Deleting item with id:", id);
      this.localProducts = this.localProducts.filter(product => product.id !== id);
    },
    addProduct(newProduct) {
      if(newProduct.isEditing){
        //logica editare
        console.log("Test Ediatrae", newProduct);
        return;
      }
      else{
      console.log('Received new product:');
      const newId = this.localProducts.length + 1;
      const newProductWithId = { id: newId, ...newProduct };
      this.localProducts.push(newProductWithId);
      console.log('Product added:', newProductWithId);
    }
    },
    editItem(product){
      console.log("Editing item...");
      // Logica pentru editare poate fi adăugată aici
      console.log(product);
      this.isEditing = true;
      this.name = product.name;
      this.price = product.price;
    },
    
  }
};
</script>

<style >

</style>
