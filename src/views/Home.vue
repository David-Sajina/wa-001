<template>	
	<v-container style="margin-top:10px; margin-bottom:10px;">
		<v-layout row wrap style>
		<details-card v-for="all in all"
			:id="all.sha"
			:det="all.commit.message"
			:key="all.sha"
		/>
        </v-layout>
	</v-container>
</template>

<script>
import axios from "axios";
import DetailsCard from "@/components/DetailsCard.vue";
export default {
	name: "Home",
	data() {
		return {
			all: [],
		};
		
	},
	async mounted() {
		const temp = await axios.get("https://api.github.com/repos/vuejs/vue/commits");
		this.all = temp.data;
		console.log("mounted", this.all);
	},
	components: {
		DetailsCard,
	},
};
</script>
