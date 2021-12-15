 <template>
     <h2> {{ CustomTitle }} !!! </h2>
     <p> {{counterrr}} <sup>2</sup> =  {{counterrr * counterrr}} </p>

     <p> {{counterrr}} <sup>2</sup> =  {{squaredCounter}} </p>
    

    <div>
        <button v-on:click="incrementa"> +1 </button>
        <button v-on:click="decrementa"> -1 </button>


         <button @click="incrementa"> +1 </button>
        <button  @click="decrementa"> -1 </button>

    </div>
 
 </template>

 <script>
import { computed } from '@vue/reactivity'
     export default{


         props:{
             titulo:String,
             start: {
                 type:Number,
                 default:100,
                 validator(value){
                     return value > 100
                 }

                 }
         },


        //name :'Patito'
        data(){
                return {
                    counterrr:10
                }
        },
        methods:{
            getSquareValue(){
                return this.counterrr * this.counterrr
            },
            incrementa(){
                this.counterrr++
            },
            decrementa(){
                this.counterrr--
            }
            
        },
        computed:{
            squaredCounter(){
                return this.counterrr * this.counterrr
            },
            CustomTitle(){
                if(this.titulo !== undefined){
                        return this.titulo
                } else{
                    return 'CounteR'
                }
            }

        }


     }

 </script>

 <style>

     button {
         margin: 0 5px;
         background-color: green;
         border-radius: 7px;
         margin: 0 15px;
         cursor: pointer;
         padding: 5px 15px;
         transition: 0.3s ease-in-out;

     }

     button:hover{
         background-color: indigo;
         transition: 0.3s ease-in-out;
     }
 
 </style>