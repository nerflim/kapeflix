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
          class="text-center"
        >
          <v-img :src="item.img"></v-img>
          <p v-text="item.name" class="font-weight-light"></p>
        </v-col>
      </v-row>
    </v-col>
    <v-col cols="12" sm="5" class="grey darken-3 elevation-5">
      <div class="pa-5">
        <p class="headline">Menu</p>

        <!-- menu -->
        <div v-for="(menu, index) in menus" :key="index">
          <p class="font-regular subtitle-1" v-text="menu.name"></p>
          <v-btn-toggle group dark v-model="active" class="d-flex">
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
            items: [
              {
                name: 'Caramel Frappuccino',
                img: '/assets/blended-coffee/caramelfrapp.png'
              },
              {
                name: 'Coffee Frappuccino',
                img: '/assets/blended-coffee/coffeefrapp.png'
              },
              {
                name: 'Dark Mocha Frappuccino',
                img: '/assets/blended-coffee/darkmochafrapp.png'
              },
              {
                name: 'Espresso Frappuccino',
                img: '/assets/blended-coffee/espressofrapp.png'
              },
              {
                name: 'Java Chip Frappuccino',
                img: '/assets/blended-coffee/javachipfrapp.png'
              },
              {
                name: 'Mocha Frappuccino',
                img: '/assets/blended-coffee/mochafrapp.png'
              },
              {
                name: 'Triple Mocha Frappuccino',
                img: '/assets/blended-coffee/triplemocha.png'
              },
              {
                name: 'Ultra Caramel Frappuccino',
                img: '/assets/blended-coffee/ultracaramel.png'
              },
              {
                name: 'White Chocolate Mocha Frappuccino',
                img: '/assets/blended-coffee/whitechocolatemochafrapp.png'
              }
            ]
          }
          // {
          //   name: 'Blended Cream',
          //   items: [
          //     'Chai Frappuccino',
          //     'Double Chocolate Chip Frappuccino',
          //     'Green Tea Frappuccino',
          //     'Strawberries & Creme Frappuccino',
          //     'Vanilla Frappuccino',
          //     'White Chocolate Frappuccino'
          //   ]
          // },
          // {
          //   name: 'Iced Beverages',
          //   items: [
          //     'Cold Brew',
          //     'Cold Brew Latte',
          //     'Dark Caramel Cold Foam Nitro',
          //     'Iced Americano',
          //     'Iced Caffè Mocha',
          //     'Iced Cappuccino',
          //     'Iced Caramel Macchiato',
          //     'Iced Green Tea Latte',
          //     'Iced Latte',
          //     'Iced Shaken Lemon Tea',
          //     'Iced Shaken Tea',
          //     'Mango Passionfruit Blended Juice',
          //     'Raspberry Blackcurrant Blended Juice',
          //     'Vanilla Sweet Cream Cold Brew'
          //   ]
          // },
          // {
          //   name: 'Coffee & Espresso',
          //   items: [
          //     'Brewed Coffee',
          //     'Caffè Americano',
          //     'Caffè Latte',
          //     'Caffè Misto',
          //     'Caffè Mocha',
          //     'Cappuccino',
          //     'Caramel Macchiato',
          //     'Caramel Mocha',
          //     'Espresso',
          //     'Espresso Con Panna',
          //     'Espresso Macchiato',
          //     'Flat White',
          //     'Pumpkin Spice Latte',
          //     'White Chocolate Mocha'
          //   ]
          // },
          // {
          //   name: 'Tea & Chocolate',
          //   items: [
          //     'Caramel Signature Hot Chocolate',
          //     'Chai Tea',
          //     'Chai Tea Latte',
          //     'Classic Hot Chocolate',
          //     'Earl Grey Tea',
          //     "Emperor's Cloud and Mist Green Tea",
          //     'English Breakfast Tea',
          //     'English Breakfast Tea Latte',
          //     'Green Tea Latte',
          //     'Mint Blend Herbal Infusion',
          //     'Signature Hot Chocolate',
          //     'White Hot Chocolate'
          //   ]
          // }
        ]
      }
      // {
      //   name: 'Food',
      //   items: [
      //     {
      //       name: 'Chocolate',
      //       items: ['Signature Chocolate', 'Signature White Chocolate']
      //     },
      //     {
      //       name: 'Breads',
      //       items: [
      //         'Blueberry Ensaymada',
      //         'Caramel Cinnamon Roll',
      //         'Choco Kitkat Doughnut',
      //         'Chocolate Chip Doughnut',
      //         'Dark Almond Doughnut',
      //         'White Almond Doughnut',
      //         'White Oreo Doughnut',
      //         "Corned Beef n' Cheese Roll",
      //         'Cheezy Pork Floss'
      //       ]
      //     },
      //     {
      //       name: 'Cakes',
      //       items: [
      //         'Blueberry Cheesecake',
      //         'Choco Ferrero Cheesecake',
      //         'Choco Oreo Cheesecake',
      //         'Classic Chocolate Cake',
      //         'Dark Chocolate Cake',
      //         'Green Tea Creamcake',
      //         'Matcha Cheesecake',
      //         'Italian Tiramisu',
      //         'Oreo Cheesecake',
      //         'Perfect Chocolate Torte',
      //         'Red Velvet Cake',
      //         'Sans Rival',
      //         'Strawberry Cheesecake'
      //       ]
      //     },
      //     {
      //       name: 'Pastries',
      //       items: ['Cheezy Banana Loaf', 'Choco Melt Loaf', 'Oatmeal Cookies']
      //     }
      //   ]
      // }
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