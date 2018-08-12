<template>
    <div>
        <h1>Computed Properties Example</h1>

        <v-autocomplete
            :items="depts"
            label="Choose A Department"
            v-model="selDept"
        >
        </v-autocomplete>

        <v-autocomplete
            :items="crews"
            label="Pick A Crew"
            v-model="selCrew"
        >
        </v-autocomplete>

        <v-btn class="ml-0 primary" :disabled="!formIsValid">Continue</v-btn>
    </div>
</template>

<script>
export default {
    props: {
        data: Array
    },

    data() {
        return {
        selDept:'',
        selCrew:''
        };
    },

    computed: {
        depts: function() {
            return this.data.map(dc => dc.dept );
        },
        crews: function() {
            return this.data.filter(dc => dc.dept === this.selDept).map(dc => dc.crew);
        },

        formIsValid: function() {
            return this.selDept!=='' && this.selCrew!=='';

        }
    }

}
</script>

<style>

</style>
