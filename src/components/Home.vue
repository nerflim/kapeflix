<template>
  <v-row no-gutters class="grey darken-4 white--text" style="height: 100%">
    <v-col cols="12" sm="7" class="pa-5" v-if="!activeMenu"></v-col>
    <v-col cols="12" sm="7" class="pa-5" v-else>
      <p class="font-thin title" v-text="activeMenu.name"></p>

      <!-- menu -->
      <v-row>
        <v-col
          cols="12"
          sm="3"
          v-for="(item, index) in activeMenu.items"
          :key="index"
          v-text="item"
        ></v-col>
      </v-row>
    </v-col>
    <v-col cols="12" sm="5" class="grey darken-3 elevation-5">
      <div class="pa-5">
        <p class="headline">Menu</p>

        <!-- menu -->
        <div v-for="(menu, index) in menus" :key="index">
          <p class="font-regular subtitle-1" v-text="menu.name"></p>
          <v-btn-toggle group dark v-model="active">
            <v-row>
              <v-col
                cols="12"
                sm="4"
                v-for="(item, i) in menu.items"
                :key="i"
                class="font-weight-light body-2"
              >
                <v-btn
                  v-text="item.name"
                  color="brown lighten-2"
                  active-class="brown lighten-2 brown--text text--darken-4"
                  text
                  depressed
                  tile
                  type="button"
                  :value="item.name"
                ></v-btn>
              </v-col>
            </v-row>
          </v-btn-toggle>

          <v-divider light class="my-5" />
        </div>
      </div>

      <NavBar />
    </v-col>
  </v-row>
</template>


<script>
import NavBar from './Nav';

export default {
  components: { NavBar },
  data: () => ({
    active: null,
    menus: [
      {
        name: 'Drinks',
        items: [
          {
            name: 'Blended Coffee',
            items: ['Lattè', 'Mocha', 'Caramel', 'Java Chip', 'Coffee Jelly']
          },
          {
            name: 'Blended Cream',
            items: [
              'Chocolate',
              'Chocolate Chip',
              'Vanilla',
              "Cookies n' Cream",
              'Green Tea Matcha',
              'Mango',
              'Banana',
              "Strawberries n' Cream",
              'Berry Mango'
            ]
          },
          {
            name: 'Blended Fruit',
            items: ['Mango Passion Fruit', 'Lemon Raspberry']
          },
          {
            name: 'Tea Latté',
            items: ['Hot or Iced', 'Green Tea Latté', 'Black Tea Latté']
          },
          {
            name: 'Tea',
            items: [
              'Chamomile',
              'Peppermint',
              'Chocolate Mint',
              'Cranberry',
              'Black Tea',
              'Green Tea'
            ]
          },
          {
            name: 'Iced Tea',
            items: ['Strawberry', 'Lemon']
          },
          {
            name: 'Fine Salt & Cheese',
            items: ['Milk Tea', 'Green Tea Matcha', 'Chocolate', 'Dark Mocha']
          },
          {
            name: 'Espresso',
            items: [
              'Espresso',
              'Espresso Macchiato',
              'Espresso con Panna',
              'Flat White',
              'Capuccino',
              'Caffè Latté',
              'Caffè Mocha',
              'Caramel Macchiato',
              'White Chocolate Mocha',
              'Caffè Americano'
            ]
          },
          {
            name: 'Brewed Coffee',
            items: ['Brewed Coffee', 'Caffè con Leche']
          }
        ]
      },
      {
        name: 'Food',
        items: [
          {
            name: 'Chocolate',
            items: ['Signature Chocolate', 'Signature White Chocolate']
          },
          {
            name: 'Breads',
            items: [
              'Blueberry Ensaymada',
              'Caramel Cinnamon Roll',
              'Choco Kitkat Doughnut',
              'Chocolate Chip Doughnut',
              'Dark Almond Doughnut',
              'White Almond Doughnut',
              'White Oreo Doughnut',
              "Corned Beef n' Cheese Roll",
              'Cheezy Pork Floss'
            ]
          },
          {
            name: 'Cakes',
            items: [
              'Blueberry Cheesecake',
              'Choco Ferrero Cheesecake',
              'Choco Oreo Cheesecake',
              'Classic Chocolate Cake',
              'Dark Chocolate Cake',
              'Green Tea Creamcake',
              'Matcha Cheesecake',
              'Italian Tiramisu',
              'Oreo Cheesecake',
              'Perfect Chocolate Torte',
              'Red Velvet Cake',
              'Sans Rival',
              'Strawberry Cheesecake'
            ]
          },
          {
            name: 'Pastries',
            items: ['Cheezy Banana Loaf', 'Choco Melt Loaf', 'Oatmeal Cookies']
          }
        ]
      }
    ]
  }),
  computed: {
    activeMenu() {
      return this.menus
        .map(menu => menu.items)
        .flat()
        .filter(menu => menu.name === this.active)[0];
    }
  }
};
</script>