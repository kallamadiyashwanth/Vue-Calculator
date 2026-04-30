<template>
    <div class="container">
        <div class="calculator">
            <input type="text" v-model="display" readonly />
            
            <button @click="clear" class = "clear-btn">Clear</button>
            <div class="buttons">
            <button @click="append('7')">7</button>
            <button @click="append('8')">8</button>
            <button @click="append('9')">9</button>
            <button @click="append('/')" class = "operator-btn">/</button>
            <button @click="append('4')">4</button>
            <button @click="append('5')">5</button>
            <button @click="append('6')">6</button>
            <button @click="append('*')" class = "operator-btn">*</button>
            <button @click="append('1')">1</button>
            <button @click="append('2')">2</button>
            <button @click="append('3')">3</button>
            <button @click="append('-')" class = "operator-btn">-</button>
            <button @click="append('.')">.</button>
            <button @click="append('0')">0</button>
            <button @click="calculate()" class = "equals-btn">=</button>
            <button @click="append('+')" class = "operator-btn">+</button>
            </div>
        </div>
    </div>
</template>

<style scoped>
.container {
    display: flex;
    justify-content: center;
    align-items: center;
    min-height: 100vh;
    background: #f4f4f4;
}

.calculator {
    background: #505050;
    padding: 20px;
    border-radius: 12px;
    width: 100%;
    max-width: 320px;
}   

input {
    width: 100%;
    height: 60px;
    font-size: 22px;
    text-align: right;
    margin-bottom: 15px;
    border-radius: 8px;
    border: none;
    padding: 0;
}   

.clear-btn{
    width: 100%;
    background-color: #f44336; 
    color: #fff;
    margin-bottom: 10px;
}

.buttons {
    display: grid;
    grid-template-columns: repeat(4, 1fr);
    gap: 10px;
}

button {
    height: 50px;
    font-size: 18px;
    border-radius: 8px;
    border: none;
    cursor: pointer;
    background: #eee;
    transition: 0.2s;
}

button:hover {
    opacity: 0.8;
}

.operator-btn {
    background-color: orange; 
    color: white;
}

.equals-btn {
    background-color: green;
    color: white;
}

</style>

<script setup>
    import { ref } from 'vue';

    const display = ref('');

    const append = (value) => {
        display.value += value;
    };

    const clear = () => {
        display.value = '';
    };

    const calculate = () => {
        try {
            display.value = eval(display.value);
        } catch (error) {
            display.value = 'Error';
        }
    };

</script>