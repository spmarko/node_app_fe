<template>
    <div class="container">
        <p>This is my data container!</p>
        <div v-for="(item,index) in myData" :key="index">
            {{ item.FirstName + " " +item.LastName + " " + item.Address + " " + item.City}}
           
        </div>
    </div>
</template>

<script>
export default {
    data(){
        return {
            myData: null,
        }
    },
    name: "IndexPage",
    props: {
        msg: String
    },
    async beforeMount(){
        let api = "/api/testdata";
        const response = await fetch(api)
        const data = await response.json();

        this.myData = data;
        console.log(this.myData)
    }
}
</script>