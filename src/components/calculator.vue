<template>
    <body>
        <div class="grid grid-cols-4 w-[300px] h-auto mx-auto gap-4">
            <div class="col-span-4 px-5 bg-gray-100 text-2xl py-5 rounded-xl">{{current || 0}}</div>
            <div class="text-gray-800 bg-gray-300 text-center rounded-full py-5" @click="clear">C</div>
            <div class="text-gray-800 bg-gray-300 text-center rounded-full py-4">+/-</div>
            <div class="text-gray-800 bg-gray-300 text-center rounded-full py-5" @click="percent">%</div>
            <div class="text-white bg-orange-400 text-center rounded-full py-5" @click="divide">/</div>
            <div class="text-white bg-gray-600 text-center rounded-full py-5" @click="append(7)">7</div>
            <div class="text-white bg-gray-600 text-center rounded-full py-5" @click="append(8)">8</div>
            <div class="text-white bg-gray-600 text-center rounded-full py-5" @click="append(9)">9</div>
            <div class="text-white bg-orange-400 text-center rounded-full py-5" @click="times">x</div>
            <div class="text-white bg-gray-600 text-center rounded-full py-5" @click="append(4)">4</div>
            <div class="text-white bg-gray-600 text-center rounded-full py-5" @click="append(5)">5</div>
            <div class="text-white bg-gray-600 text-center rounded-full py-5" @click="append(6)">6</div>
            <div class="text-white bg-orange-400 text-center rounded-full py-5" @click="minus">-</div>
            <div class="text-white bg-gray-600 text-center rounded-full py-5" @click="append(1)">1</div>
            <div class="text-white bg-gray-600 text-center rounded-full py-5" @click="append(2)">2</div>
            <div class="text-white bg-gray-600 text-center rounded-full py-5" @click="append(3)">3</div>
            <div class="text-white bg-orange-400 text-center rounded-full py-5" @click="add">+</div>
            <div class="col-span-2 text-white bg-gray-600 rounded-full py-5 px-5" @click="append(0)">0</div>
            <div class="text-white bg-gray-600 text-center rounded-full py-5" @click="doat('.')">.</div>
            <div class="text-white bg-orange-400 text-center rounded-full py-5" @click="equl">=</div>
        </div>
    </body>
    
</template>

<script>
export default {
    name,
    data(){
        return{
           current : '',
           operator : null,
           pervious : null,
           operatorClick : false,
        }
    },
    methods: {
        clear(){
            this.current = ''
        },
        percent(){
            this.current = `${parseFloat(this.current) / 100}`
        },
        append(number){
            if(this.operatorClick){
                this.current = '';
                this.operatorClick = false;
            }
            this.current = `${this.current}${number}`
        },
        doat(){
            if(this.current.indexOf('.')=== -1){
                this.append('.');
            }
        },

        set(){
            this.pervious = this.current;
            this.operatorClick = true;
        },

        add(){
            this.operator = (a , b) => a+b;
            this.set();
        },
        divide(){
             this.operator = (a , b) => a/b;
             this.set();
        },
        minus(){
            this.operator = (a , b) => b-a;
            this.set();
        },
        times(){
            this.operator = (a , b) => a*b;
            this.set();
        },
        equl(){
            this.current = this.operator(parseFloat(this.current) , parseFloat(this.pervious))
        }
    },
}
</script>
