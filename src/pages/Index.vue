<template>
  <div>
    <div class="top-menu">
      <q-tabs v-model="category" class="bg-secondary">
        <q-tab name="screen" label="Screens" />
        <q-tab name="peripherals" label="Peripherals" />
        <q-tab name="pc" label="Computers" />
        <q-tab name="laptop" label="Laptops" />
        <q-btn
          color="secondary"
          icon="add_shopping_cart"
          @click="showcart()"
          class="q-pl-md"
        />
      </q-tabs>
    </div>
    <div class="q-pa-xl row">
      <div v-for="(item, id) in newproducts" :key="id" class="col-4 q-pa-md">
        <q-card>
          <q-img :src="item.img">
            <div class="absolute-top text-h6">{{ item.name }}</div>
          </q-img>

          <q-expansion-item>
            <q-card>
              <q-card-section>
                <p>Categoría : {{ item.category }}</p>
                <p>Definición : {{ item.def }}</p>
                <p>Stock : {{ item.stock }}</p>
                <p>Precio : {{ item.price }}</p>
                <q-btn-group>
                  <q-btn
                    color="secondary"
                    icon="add_shopping_cart"
                    @click="addItem(item.name)"
                  />
                  <q-btn
                    color="secondary"
                    icon="remove_shopping_cart"
                    @click="deleteItem(item.name)"
                  />
                </q-btn-group>
              </q-card-section>
            </q-card>
          </q-expansion-item>
        </q-card>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      category: "screen",
      newproducts: [],
      cart: [],
      msg: "",
      products: [
        {
          name: "Screen 1",
          category: "screen",
          stock: 25,
          def: "item definition",
          price: "45",
          img: "images/cart-icon.png",
        },
        {
          name: "Screen 2",
          category: "screen",
          stock: 25,
          def: "item definition",
          price: "4545",
          img: "images/cart-icon.png",
        },
        {
          name: "Screen 3",
          category: "screen",
          stock: 25,
          def: "item definition",
          price: "45",
          img: "images/cart-icon.png",
        },
        {
          name: "Screen 4",
          category: "screen",
          stock: 25,
          def: "item definition",
          price: "4545",
          img: "images/cart-icon.png",
        },
        {
          name: "Peripheral 1",
          category: "peripherals",
          stock: 25,
          def: "item definition",
          price: "454",
          img: "images/cart-icon.png",
        },
        {
          name: "Peripheral 2",
          category: "peripherals",
          stock: 25,
          def: "item definition",
          price: "454",
          img: "images/cart-icon.png",
        },
        {
          name: "Peripheral 3",
          category: "peripherals",
          stock: 25,
          def: "item definition",
          price: "545",
          img: "images/cart-icon.png",
        },
        {
          name: "PC 1",
          category: "pc",
          stock: 25,
          def: "item definition",
          price: "45",
          img: "images/cart-icon.png",
        },
        {
          name: "PC 2",
          category: "pc",
          stock: 25,
          def: "item definition",
          price: "3462",
          img: "images/cart-icon.png",
        },
        {
          name: "PC 3",
          category: "pc",
          stock: 25,
          def: "item definition",
          price: "234",
          img: "images/cart-icon.png",
        },
        {
          name: "PC 4",
          category: "pc",
          stock: 25,
          def: "item definition",
          price: "3453",
          img: "images/cart-icon.png",
        },
        {
          name: "PC 5",
          category: "pc",
          stock: 25,
          def: "item definition",
          price: "345345",
          img: "images/cart-icon.png",
        },
        {
          name: "Laptop 1",
          category: "laptop",
          stock: 25,
          def: "item definition",
          price: "34532",
          img: "images/cart-icon.png",
        },
        {
          name: "Laptop 2",
          category: "laptop",
          stock: 25,
          img: "",
          def: "item definition",
          price: "34534",
          img: "images/cart-icon.png",
        },
        {
          name: "Laptop 3",
          category: "laptop",
          stock: 25,
          img: "",
          def: "item definition",
          price: "3423",
          img: "images/cart-icon.png",
        },
      ],
    };
  },
  watch: {
    category() {
      this.filterCat();
    },
  },
  methods: {
    filterCat() {
      this.newproducts = this.products.filter(
        (product) => product.category === this.category
      );
    },
    addItem(item) {
      this.cart.push(item);
      console.log(this.cart);
      console.log(item);
    },
    deleteItem(item) {
      let index = this.cart.indexOf(item);
      if (index !== -1) {
        this.cart.splice(index, 1);
        console.log(this.cart);
        console.log(item);
      }
    },
    showcart() {
      console.log(this.cart);
      if (this.cart.length == 0) {
        this.msg = "YOUR CART IS EMPTY, ADD SOME ITEMS";
        console.log(this.msg);
      } else {
        this.msg = this.cart;
      console.log(this.msg);
      }
    },
  },
  created() {
    this.filterCat();
  },
};
</script>
