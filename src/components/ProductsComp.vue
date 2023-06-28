<template>
    <div>
        <div class="container">
            <div class="row">
                <div class="col" v-for="item in data" :key="item.id">
                    <div class="card" style="width: 18rem;">
                        <img :src="item.image" class="card-img-top" :alt="item.name">
                        <div class="card-body">
                          <h1>{{ item.name }}</h1>
                          <h4>{{ item.price }}</h4>
                        </div>
                      </div>
                </div>
            </div>
        </div>
        
    </div>
</template>

<script>
    export default {
      data(){
        return{
            data:[]
        }
      } ,
      methods: {
        async fetchData(){
           const res = await("https://imtiyaaz-d.github.io/vue-server/user.json");
           let parsedData = await res.json()
           this.data = parsedData.products;
        }
      },
      mounted(){
        this.fetchData()
      } 
    }
</script>

<style scoped>

</style>