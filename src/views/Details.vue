<template>
    <div>
        <v-card v-if="test.commit">
            <v-card-title>Sha: {{ test.sha }}</v-card-title>
            <v-card-subtitle>Author: {{ test.commit.author.name}}</v-card-subtitle>
            <v-card-subtitle>Email: {{ test.commit.author.email}}</v-card-subtitle>
            <v-card-subtitle>Date: {{ test.commit.author.date}}</v-card-subtitle>
            <v-card-subtitle>Message: {{test.commit.message}}</v-card-subtitle>
           
           <v-spacer></v-spacer> <v-btn color="#026fa6" style="margin-left:10px; margin-bottom:10px;" @click="home()">Go back</v-btn>
        </v-card>
    </div>
</template>

<script>

import axios from "axios";
	export default {
	name: "Home",
	data() {
		return {
			all: [],
            test: [],
            help:0,
		};
		
	},
	async mounted() {
		const temp = await axios.get("https://api.github.com/repos/vuejs/vue/commits");
		this.all = temp.data;
		console.log("details", this.$route.params.sha_id);
        console.log(this.all);
        for(let i=0; i<this.all.length; i++){
            if(this.all[i].sha == this.$route.params.sha_id)this.help=i;
        }
        console.log("ito", this.all[this.help]);
        this.test = this.all[this.help];
        console.log("test",this.test)
	},
    methods:
   { home(){
        this.$router.replace({ name: "Home" });
    }}
};
</script>

