<template>
    <div>
        <select name="Countyr" id="country" @change="onChange" v-model="selected" class="form-select mt-10 block w-full border p-3 rounded">
        <option value="0">Select Country</option>

        <option :value="country.ID" v-for="country in countries" :key="country.ID">
        {{country.Country}}
        </option>
        </select>
    </div>
</template>
<script>

export default {
    name:'CountrySelect',
    props:['countries'],
    data(){
        return{
            selected:0
        }
    },
    methods:{
        onChange(){
            const country=this.countries.find((item)=>item.ID===this.selected)
            this.$emit('countryChanged',country)
        }
    }
    }
</script> 
 