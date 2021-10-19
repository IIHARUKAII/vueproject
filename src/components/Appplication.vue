<template >
    <div class="box">
        <h3 class="title"> {{ movieId }} </h3>
        <h1 id="price">Count:{{status.count}}, Price:{{status.price}} </h1>
        <movie @chooseMovie="handleChooseMovie" :movieId="movieId"/>
        <seat 
        :movieId="movieId" 
        @chooseSeat="handleChooseSeat"
        :selectSeats="selectSeats"
        />
        <button class="buy" type="button" @click="alert">Buy Ticket</button>
        <!-- <button class="buy">Buy Ticket</button> -->
    </div>
</template>
<script>
import Movie from '../components/Movie.vue'
import Seat from '../components/Seat.vue'

export default {
   components:{ Movie, Seat },
   data(){
       return{
           movieId: '',
           selectSeats: [],
           status: {count:0, price: 0}
       }
   },
   methods:{
       handleChooseMovie(movieId){
           if(this.status.count){
               if(confirm('Data will be lost???')){
                   this.status = { count:0, price :0}
                   this.selectSeats = []
               }else{
                   return false
               }
           }
           this.movieId = movieId
       },
       handleChooseSeat(seat){
           const ids = this.selectSeats.map(s => s.id )
           const idx = ids.indexOf(seat.id)
           if(idx === -1 ){
                this.selectSeats.push(seat)
           }else{
               this.selectSeats.splice(idx, 1)
           }

           this.status = this.selectSeats.reduce((summary, s) => {
               summary.count ++
               summary.price += s.price
               return summary
           },{count:0, price:0})
          
           console.log(this.selectSeat.length)
       },
       alert(){
           return alert("Thank You for buy ticket, you ticket price is" + this.status.price);
       }
       
   }
}
</script>
<style >
    #price{
        font-weight: bold;  
        font-size: 50px;
    }
    .buy{
       transition-duration: 0.4s;
       background-color: white; /* Green */
        border: none;
        color: black;
        padding: 15px 32px;
        text-align: center;
        text-decoration: none;
        display: inline-block;
        font-size: 16px;
    }
    .buy:hover{
        background-color: lightgray; /* Green */
        color:black;
    }
</style>