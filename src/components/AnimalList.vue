<template>
    <div>
        <h3>Animal list</h3>

          <table border =1>
        <thead>
            <th>Index</th>
            <th>Spicies</th>
            <th>Name</th>
            <th>Date of birth</th>
        </thead>
        <tbody>
            <tr v-for="(animal,index) in animalList" :key="index">
                <td>{{index + 1}}</td>
                <td>{{animal.spicies}}</td>
                <td>{{animal.name}}</td>
                
                <td v-if= "animal.dateOfBirth !== ''">{{animal.dateOfBirth}}</td>
                <td v-if= "animal.dateOfBirth === ''">Nepoznat</td>

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
export default {
     methods:{
            
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
            animalList: [
                {spicies: 'sisar',name: 'Brka', dateOfBirth:'11.10.2016'},
                {spicies: 'glodar',name: 'Miki', dateOfBirth:'11.10.2014'},
                {spicies: 'vodozemac',name: 'Shiki', dateOfBirth:'11.5.2012'},
                {spicies: 'dinosaurus',name: 'Rez', dateOfBirth:'11.9.2011'},
                {spicies: 'sisar',name: 'Brka', dateOfBirth:'11.5.2011'},
                {spicies: 'sisar',name: 'Aca', dateOfBirth:''}
            ],
            
        }
    }
  
}
</script>
