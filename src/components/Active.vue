<template>
  <div>
    <div class="d-flex flex-row-reverse">
      <v-btn icon color="brown" @click="$emit('close')">
        <v-icon>mdi-close</v-icon>
      </v-btn>
    </div>
    <v-row>
      <v-col cols="12" sm="6" class="brown--text text--lighten-2">
        <p v-text="item.name" class="title"></p>
        <p v-text="item.desc" class="caption"></p>

        <p>Available sizes:</p>

        <!-- sizes -->
        <v-card class="d-flex flex-row mb-6" tile flat color="transparent">
          <v-btn-toggle v-model="size" tile color="brown" group>
            <v-btn
              v-for="(sz, i) in sizes"
              :key="i"
              color="brown--text text--lighten-1"
              height="auto"
              :value="sz.id"
            >
              <div class="pa-2 d-flex flex-column">
                <p v-text="sz.name"></p>
                <p class="caption mb-0">{{sz.ml}}mL</p>
              </div>
            </v-btn>
          </v-btn-toggle>
        </v-card>

        <!-- quantity -->
        <v-menu offset-y>
          <template v-slot:activator="{ on }">
            <v-btn outlined depressed color="brown" large v-on="on" class="mr-5">Qty: {{quantity}}</v-btn>
          </template>
          <v-list dark>
            <v-list-item v-for="(qty, index) in quantities" :key="index" @click="quantity = qty">
              <v-list-item-title v-text="qty"></v-list-item-title>
            </v-list-item>
          </v-list>
        </v-menu>

        <!-- add to cart -->
        <v-btn
          outlined
          depressed
          large
          color="brown"
          :disabled="!quantity || !size"
          @click="addToCart()"
        >
          Add to cart
          <v-icon right>mdi-cart-outline</v-icon>
        </v-btn>
      </v-col>
      <v-col cols="12" sm="6">
        <v-img :src="item.img"></v-img>
      </v-col>
    </v-row>
    <v-divider dark class="my-4"></v-divider>
  </div>
</template>

<script>
import uniqid from 'uniqid';

export default {
  props: ['item'],
  data: () => ({
    size: null,
    sizes: [
      { id: uniqid(), name: 'Tall', ml: 354, icon: '' },
      { id: uniqid(), name: 'Grande', ml: 473, icon: '' },
      { id: uniqid(), name: 'Venti', ml: 591, icon: '' }
    ],
    quantity: 0,
    quantities: [1, 2, 3, 4, 5]
  }),
  methods: {
    addToCart() {
      this.$emit('addToCart', {
        item: this.item,
        qty: this.quantity,
        size: this.sizes.filter(size => size.id === this.size)[0]
      });
    }
  }
};
</script>