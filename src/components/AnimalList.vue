<template>
    <div>
        <h3>Animal list</h3>

          <table border =1>
        <thead>
            \
            <th>Spicies</th>
            <th>Name</th>
            <th>Date of birth</th>
        </thead>
        <tbody>
            <tr v-for="(animalList,index) in animalList" :key="index">
                <td>{{key + 1}}</td>
                <td>{{animalList.spicies}}</td>
                <td>{{animalList.name}}</td>
                <td>{{animalList.dateOfBirth}}</td>
                

            </tr>
        </tbody>
</table>

    </div>
  
</template>

<script>
export default {
    data(){
        return {
            animalList: [
                {spicies: 'sisar',name: 'Brka', dateOfBirth:'11.10.2016'},
                {spicies: 'glodar',name: 'Miki', dateOfBirth:'11.10.2014'},
                {spicies: 'vodozemac',name: 'Shiki', dateOfBirth:'11.5.2012'},
                {spicies: 'dinosaurus',name: 'Rez', dateOfBirth:'11.9.2011'},
                {spicies: 'sisar',name: 'Brka', dateOfBirth:'11.5.2011'},
            ]
        }
    }
  
}
</script>
