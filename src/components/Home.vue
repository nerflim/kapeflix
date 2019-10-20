<template>
  <v-row no-gutters class="grey darken-4 white--text flex-row-reverse" style="height: 100%">
    <v-col cols="12" sm="5" class="grey darken-3 elevation-5">
      <div class="pa-5">
        <p class="headline">Menu</p>

        <!-- menu -->
        <div v-for="(menu, index) in menus" :key="index">
          <p class="font-regular subtitle-1" v-text="menu.name"></p>
          <v-row>
            <v-col
              cols="12"
              md="6"
              lg="4"
              v-for="(item, i) in menu.items"
              :key="i"
              class="font-weight-light"
            >
              <v-btn
                v-text="item.name"
                :color="item.id === active ? 'brown brown--text text--darken-4': 'brown lighten-2'"
                :text="item.id !== active"
                depressed
                tile
                block
                large
                type="button"
                @click="setActiveMenu(item.id)"
              ></v-btn>
            </v-col>
          </v-row>

          <v-divider light class="my-5" />
        </div>
      </div>
    </v-col>
    <v-col cols="12" sm="7" class="pa-5" v-if="!activeMenu"></v-col>
    <v-col cols="12" sm="7" class="pa-5" v-else>
      <p class="font-thin title" v-text="activeMenu.name"></p>

      <!-- menu -->
      <v-scale-transition origin="center center" hide-on-leave>
        <Active :item="activeItem" v-if="activeItem" @close="activeItemId = null" />
      </v-scale-transition>

      <v-row>
        <v-col
          cols="6"
          md="3"
          sm="4"
          v-for="(item, index) in activeMenu.items"
          :key="index"
          class="text-center"
        >
          <v-hover v-slot:default="{ hover }">
            <v-card
              flat
              tile
              :color="activeItemId === item.id ? 'brown darken-3' : 'transparent'"
              link
              @click="setActiveItem(item.id)"
            >
              <v-img :src="item.img"></v-img>
              <p
                v-text="item.name"
                class="font-weight-light brown--text"
                :class="hover ? '' : 'text--lighten-2'"
              ></p>
            </v-card>
          </v-hover>
        </v-col>
      </v-row>
    </v-col>
  </v-row>
</template>


<script>
import Active from './Active';
import uniqid from 'uniqid';

export default {
  components: { Active },
  data: () => ({
    active: null,
    activeItemId: null,
    menus: [
      {
        name: 'Drinks',
        items: [
          {
            id: uniqid(),
            name: 'Blended Coffee',
            items: [
              {
                id: uniqid(),
                name: 'Caramel Frappuccino',
                desc:
                  'This delectable treat is hands down our most popular Frappuccino blended beverage. And it’s not hard to see why. The coffee is bold but easy-drinking. The caramel lends a distinct buttery sweetness. The fluffy swirl of whipped cream adds just the right touch of decadence. That’s tough to beat by any measure.',
                img: '/assets/blended-coffee/caramelfrapp.png'
              },
              {
                id: uniqid(),
                name: 'Coffee Frappuccino',
                desc:
                  'This is our original Frappuccino blended beverage – the one that reinvented summertime coffee for millions of coffee lovers around the world. It sparked immediate accolades and lasting devotion. Because as with any true original, the delicious taste of this refreshingly cool coffee really stands the test of time.',
                img: '/assets/blended-coffee/coffeefrapp.png'
              },
              {
                id: uniqid(),
                name: 'Dark Mocha Frappuccino',
                desc:
                  "If you love fun in the  sun, then this deliciously decadent beverage is made for you. It's sweet, creamy and cold – just the way a good summer treat should be. And it serves up the rich, satisfying taste of dark chocolate and coffee. Pure indulgence for pure enjoyment.",
                img: '/assets/blended-coffee/darkmochafrapp.png'
              },
              {
                id: uniqid(),
                name: 'Espresso Frappuccino',
                desc:
                  'Much like our original Coffee Frappuccino blended beverage, this delectable indulgence is a refreshing blend of our dark-roasted coffee, milk and ice. However the added shot of our rich and smooth Espresso Roast creates a bolder coffee flavour that espresso lovers get really excited about.',
                img: '/assets/blended-coffee/espressofrapp.png'
              },
              {
                id: uniqid(),
                name: 'Java Chip Frappuccino',
                desc:
                  'We created this wondrously decadent beverage for those who love the taste of chocolate – and lots of it – with their iced coffee. Rich, chocolatey chips punctuate a cool, refreshing blend of coffee and mocha flavours. And in case that isn’t enough chocolatey goodness for you, we finish our sweetened whipped cream topping with a deliciously sweet chocolate-flavoured drizzle.',
                img: '/assets/blended-coffee/javachipfrapp.png'
              },
              {
                id: uniqid(),
                name: 'Mocha Frappuccino',
                desc:
                  "If making the most of sunny weather is a priority for you in the summer, this delicious, decadent beverage should come to mind. It's sweet, creamy and cold – just the way a good summer treat should be. And it serves up the rich, satisfying taste of chocolate and coffee. Pure indulgence for pure enjoyment.",
                img: '/assets/blended-coffee/mochafrapp.png'
              },
              {
                id: uniqid(),
                name: 'Triple Mocha Frappuccino',
                desc:
                  'Mocha Frappuccino is enveloped between layers of whipped cream that’s infused with cold brew, white chocolate mocha and dark caramel. On each layer of whipped cream is a dollop of rich dark mocha sauce. These layers ensure each sip is as good as the last; all the way to the end.',
                img: '/assets/blended-coffee/triplemocha.png'
              },
              {
                id: uniqid(),
                name: 'Ultra Caramel Frappuccino',
                desc:
                  'Dark caramel coffee Frappuccino is enveloped between layers of whipped cream that’s infused with cold brew, white chocolate and dark caramel. And on each layer of whipped cream sits a dollop of dark caramel sauce. These layers ensure each sip is as good as the last; all the way to the end.',
                img: '/assets/blended-coffee/ultracaramel.png'
              },
              {
                id: uniqid(),
                name: 'White Chocolate Mocha Frappuccino',
                desc:
                  'Both are creamy and delicious. That goes without saying. But white chocolate charms the palate with an extra buttery quality that inspires devotion. Those who like it absolutely love our White Chocolate Mocha Frappuccino® blended coffee.',
                img: '/assets/blended-coffee/whitechocolatemochafrapp.png'
              }
            ]
          },
          {
            id: uniqid(),
            name: 'Blended Cream',
            items: [
              {
                id: uniqid(),
                name: 'Chai Frappuccino',
                desc:
                  'In India, roadside vendors can be found creating an aromatic concoction of black tea infused with the exotic flavours of cardamom, cinnamon and black pepper over a hot stove. But if you want to enjoy the sweet and spicy taste of chai tea in summer, we recommend dropping into your local Starbucks to try this icy take on the traditional beverage. You’ll love it just as much cold.',
                img: '/assets/blended-cream/chaifrapp.png'
              },
              {
                id: uniqid(),
                name: 'Double Chocolate Chip Frappuccino',
                desc:
                  'What makes this cool beverage doubly delicious? The flavour of chocolate and more chocolate – something we just can’t get enough of. There’s the rich, creamy taste of mocha-flavoured sauce blended with milk. Plus chocolaty chips in every sip. Well deserving of two enthusiastic thumbs up.',
                img: '/assets/blended-cream/doublechocchipfrapp.png'
              },
              {
                id: uniqid(),
                name: 'Green Tea Frappuccino',
                desc:
                  'Although matcha tea is best known for its central role in the serene ritual known as the Japanese tea ceremony, tea drinkers all over the world have come to enjoy the gentle, uplifting taste of this finely-powdered green tea in their own way. We particularly like the way it blends with milk and ice in this refreshing Frappuccino® blended beverage. And we think you will too.',
                img: '/assets/blended-cream/greenteafrapp.png'
              },
              {
                id: uniqid(),
                name: 'Strawberries & Creme Frappuccino',
                desc:
                  'Inspired by the classic, country-style treat of strawberries and cream, we’ve created a refreshing beverage that sweetens any summer activity. From a lazy afternoon picnic to a raucous sporting event, you’ll welcome the fruity flavours of this icy sensation more than a cool breeze on a sweltering day.',
                img: '/assets/blended-cream/strawberriescreamfrapp.png'
              },
              {
                id: uniqid(),
                name: 'Vanilla Frappuccino',
                desc:
                  'It took Europeans about 300 years to discover the secret to growing vanilla outside its native Mexico – and then only after a 12-year-old boy figured out how to do it. A surprising turn of events, no doubt. But one that we’re very grateful for. Because without this tasty revelation, we could not offer this splendid iced beverage.',
                img: '/assets/blended-cream/vanillafrapp.png'
              },
              {
                id: uniqid(),
                name: 'White Chocolate Frappuccino',
                desc:
                  'There’s something grand and glorious about the taste of white chocolate. Maybe because its rich, buttery flavour is so supremely decadent, you imagine it an exclusive treat of royal courts and other fancy places. Luckily anyone can enjoy its sumptuous pleasures in this magnificent iced beverage. Smooth and creamy, it’s the height of cool elegance – and it’s yours to savour. Did you know? Though this delicious beverage is made with white chocolate flavoured syrup, it’s completely coffee – and caffeine – free.',
                img: '/assets/blended-cream/whitechocolatemochafrapp.png'
              }
            ]
          }
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
        .filter(menu => menu.id === this.active)[0];
    },
    activeItem() {
      return this.activeMenu.items.filter(
        item => item.id === this.activeItemId
      )[0];
    }
  },
  methods: {
    setActiveItem(id) {
      this.activeItemId = this.activeItemId !== id ? id : null;
    },
    setActiveMenu(id) {
      this.active = id;
      this.activeItemId = null;
    }
  }
};
</script>