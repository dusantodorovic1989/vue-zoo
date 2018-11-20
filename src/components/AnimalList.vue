<template>
    <div>
          <h3>Add animal</h3>
     <form @submit.prevent='addAnimal'>
         <label>Spicies</label>
         <input v-model="newAnimal.spicies" placeholder="Spicies"/><br>
         <label>Name</label>
         <input v-model="newAnimal.name" placeholder="Name"/><br>
         <label>Date of birth</label>
         <input v-model="newAnimal.dateOfBirth" placeholder="Date of birth"/><br>

         <select v-model="newAnimal.sector">
            <option disabled value="">Please select one</option>
            <option v-for='(sector,index) in sectors' :key="index" :value ="sector">{{sector.name}}</option>
           
            </select>
        
         

         <button type='sibmit'>ADD ANIMAL</button>
        
    </form>
        <h3>Animal list</h3>

          <table border =1>
        <thead>
            <th>Index</th>
            <th>Spicies</th>
            <th>Name</th>
            <th>Date of birth</th>
            <th>Sector</th>
        </thead>
        <tbody>
            <tr v-for="(animal,index) in animalList" :key="index">
                <td>{{index + 1}}</td>
                <td>{{animal.spicies}}</td>
                <td>{{animal.name}}</td>
                
                <td v-if= "animal.dateOfBirth !== ''">{{animal.dateOfBirth}}</td>
                <td v-if= "animal.dateOfBirth === ''">Nepoznat</td>

                <td>{{animal.sector.name}}</td>

                 <td>
                    <button @click="removeAnimal(animal)">Remove</button>
                </td>

                <td>
                    <button @click="moveToTop(animal)">Move to top</button>
                </td>

            </tr>
        </tbody>
</table>

    </div>
  
</template>

<script>
const sectors = [
    {name:'Water-animal',surface: 'Water'},
    {name:'Air-animal',surface: 'Air'},
    {name:'Dinusaurusi',surface: 'All-ground'},
];
export default {
     methods:{

            addAnimal(){
                this.animalList.push(this.newAnimal);
                this.newContact = {};
            },
            removeAnimal(animal){
                let index = this.animalList.indexOf(animal);
                this.animalList.splice(index,1);
                
            },
            moveToTop(animal){
                let index1= this.animalList.indexOf(animal);
                
                
                this.animalList.splice(index1,1);
                this.animalList.unshift(animal);
            }

        },

    data(){
        return {
            sectors:sectors,
            newAnimal:{
                
            },
            animalList: [
                {spicies: 'sisar',name: 'Brka', dateOfBirth:'11.10.2016',sector:sectors[0]},
                {spicies: 'glodar',name: 'Miki', dateOfBirth:'11.10.2014',sector:sectors[0]},
                {spicies: 'vodozemac',name: 'Shiki', dateOfBirth:'11.5.2012',sector:sectors[2]},
                {spicies: 'dinosaurus',name: 'Rez', dateOfBirth:'11.9.2011',sector:sectors[2]},
                {spicies: 'sisar',name: 'Brka', dateOfBirth:'11.5.2011',sector:sectors[1]},
                {spicies: 'sisar',name: 'Aca', dateOfBirth:'',sector:sectors[0]}
            ],
            
        }
    }
  
}
</script>
