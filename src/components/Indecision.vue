<template>
  
    <img v-if="img" :src="img" alt="bg">
    <div class="bg-dark"></div>

    <div class="indecision-container">

        <input 
            v-model="question"
            type="text" 
            placeholder="Hazme una pregunta">
        <p>Recuerda terminar con un signo de interrogacion (?)</p>

        <div v-if="isValidQuestions">
             <h2>{{question}}</h2>
            <h1>{{answer === 'yes'? 'Si!!!' : 'No!!!'}}</h1>
                <!-- si! : yes -->
           <!--  no! : no -->
        </div>

    </div>

</template>

<script>
export default {
    data(){
        return {
            question:null,
            answer:null,
            img:null,
            isValidQuestions: false
        }
    },
    methods:{

        async getAnswer(){

            this.answer='Pensando...'
            const {answer,image} = await fetch('https://yesno.wtf/api').then(r => r.json())

            this.answer= answer
            this.img=image


        }


    },
    watch:{
        question(value, oldValue){

            this.isValidQuestions=false    

            if(!value.includes('?'))
            return 
            this.isValidQuestions=true
            this.getAnswer()
            //TODO Realizar peticion http
        }
    }
    
}
</script>

<style >
img, bg-dark{
        height: 100vh;
        left: 0px;
        max-height: 100%;
        max-width: 100%;
        position: fixed;
        top: 0px;
        width: 100vw;
    }
    .bg-dark{
        background-color: rgba(0,0,0,4);
    }
    .indecision-container{
        position:relative;
        z-index: 99;
    }

    input{
        width: 250px;
        padding: 10px 15px;
        border-radius: 10px;
        border: none;
        
    }
    input:focus{
        outline: rgb(255, 0, 0);
    }
    p{
        color: rgb(255, 255, 255);
        font-size: 25px;
        margin-top: 20px;
    }
    h1,h2{
        color: rgb(255, 255, 255);
    }
    h2{
        margin-top: 100px;
        font-size: 40px;
    }
    h1{
        font-size: 60px;
    }
  

</style>