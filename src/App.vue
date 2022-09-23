<script setup>
import { ref } from 'vue'
import DATA from "./assets/data/data.json"
import Main from "./components/Main.vue";


function filterByGroups(data) {
    const groups = data.reduce((currentData, person) => {
        currentData[person.group] = [];
        return currentData;
    },{});
    
		Object.keys(groups).forEach(group => {
       const students =  data.filter(person => person.group == group);
       groups[group] = students;
			 console.log(groups);

    })
    return groups
		
}


</script>



<template>

<Main></Main>

<ul class="listsBlock">	
		<li class="lists" style="list-style-type: none;" v-for=" groups in filterByGroups(DATA)">{{groups}}</li>		
</ul>



</template>


<style scoped>
.listsBlock {
    list-style-type: none;
    margin: 0px;
    padding:0px;
    overflow: hidden;
		
}
.lists {
    float: left;
		border:2px solid white;
		width: 245px;
		height: 900px;
		margin: 3px;
		padding-top: 5px;		
}

</style>
