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
				<p class="font-thin title">Menu</p>

				<!-- menu -->
				<v-row>
					<v-col cols="12" sm="4">test</v-col>
					<v-col cols="12" sm="4">test</v-col>
					<v-col cols="12" sm="4">test</v-col>
					<v-col cols="12" sm="4">test</v-col>
					<v-col cols="12" sm="4">test</v-col>
					<v-col cols="12" sm="4">test</v-col>
					<v-col cols="12" sm="4">test</v-col>
					<v-col cols="12" sm="4">test</v-col>
					<v-col cols="12" sm="4">test</v-col>
				</v-row>
			</div>

			<NavBar />
		</v-col>
	</v-row>
</template>


<script>
import NavBar from './Nav';

export default {
	components: { NavBar }
};
</script>