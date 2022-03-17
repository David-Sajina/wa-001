<template>
	<v-layout row wrap style>
		<v-card class="text-xs-center ma-3" max-width="350" style="margin-top:15px;">
			<v-card-title> {{ id }} </v-card-title>
			<v-card-subtitle> {{ det }} kn </v-card-subtitle>
			<v-card-actions>
				<router-link
					:to="{ name: 'Details', params: { sha_id: id } }"
				>
					<v-btn
        rounded
        color="primary"
        dark>Details</v-btn>
				</router-link>
			</v-card-actions>
		</v-card>
	</v-layout>
</template>
<script>
	export default {
		name: "DetailsCard",
		props: {
			id: String,
			det: String,
		},
	};
</script>

<style></style>
