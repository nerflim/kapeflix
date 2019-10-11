<template>
	<v-row no-gutters class="grey darken-4 white--text" style="height: 100%">
		<v-col cols="12" sm="7" class="pa-5">
			<p class="font-thin title">Coffee</p>

			<!-- menu -->
			<v-row>
				<v-col cols="12" sm="3">test</v-col>
				<v-col cols="12" sm="3">test</v-col>
				<v-col cols="12" sm="3">test</v-col>
				<v-col cols="12" sm="3">test</v-col>
				<v-col cols="12" sm="3">test</v-col>
				<v-col cols="12" sm="3">test</v-col>
				<v-col cols="12" sm="3">test</v-col>
				<v-col cols="12" sm="3">test</v-col>
				<v-col cols="12" sm="3">test</v-col>
				<v-col cols="12" sm="3">test</v-col>
				<v-col cols="12" sm="3">test</v-col>
				<v-col cols="12" sm="3">test</v-col>
				<v-col cols="12" sm="3">test</v-col>
			</v-row>
		</v-col>
		<v-col cols="12" sm="5" class="grey darken-3 elevation-5">
			<div class="pa-5">
				<p class="headline">Menu</p>

				<!-- menu -->
				<div v-for="(menu, index) in menus" :key="index">
					<p class="font-regular subtitle-1" v-text="menu.name"></p>
					<v-btn-toggle group dark mandatory v-model="active">
						<v-row>
							<v-col
								cols="12"
								sm="4"
								v-for="(item, index) in menu.items"
								:key="index"
								class="font-weight-light body-2"
							>
								<v-btn
									v-text="item"
									color="brown lighten-2"
									active-class="brown lighten-2 brown--text text--darken-4"
									text
									depressed
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
					'Blended Coffee',
					'Blended Cream',
					'Blended Fruit',
					'Tea Latté',
					'Tea',
					'Iced Tea',
					'Espresso',
					'Brewed Coffee'
				]
			},
			{
				name: 'Food',
				items: ['Chocolate', 'Breads', 'Cakes', 'Pastries']
			}
		]
	})
};
</script>