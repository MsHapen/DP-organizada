<script setup>
    import { defineProps, ref, computed }  from 'vue'

    const props = defineProps({
        data: Object,
    });
    props.data.currentStep--;

    const data = ref(props.data);

    const cssStyle = computed(() => {
        return {
            '--active-color': data.value.activeColor,
            '--passive-color': data.value.passiveColor,
        }
    });

    const nextStep = () => {
        if (data.value.currentStep < data.value.steps.length){
            data.value.currentStep++;
        }
    }

    const previousStep = () => {
        if (data.value.currentStep > 0){
            data.value.currentStep--;
        }
    }

    defineExpose({
        nextStep,
        previousStep,
    });
</script>

<template>
    <div class="steps-container" :style="cssStyle">
        <ul class="steps-list">
            <li class="step" v-for="(step, index) in data.steps" :key="index"
            :class="(index == data.currentStep) ? 'step-active' : '', (index < data.currentStep) ? 'step-done' : ''">
                <div class="step-bubble"></div>

            </li>
        </ul>
    </div>
    
</template>

<style>

.steps-container {
    width: 95%;
    margin: 0 auto;
}
.step-list{
    display: flex;
    list-style: none;
}
.step{
    display: flex;
    align-items: center;
    flex-grow: 1;
    max-width: 100%;
    position: relative;
    height: 60px;
}
.step-bubble{
    width: 35px;
    height: 35px;
    border-radius: 50%;
    background-color: var(--passive-color);
    transition: all .3 ease;
    display: flex;
    align-items: center;
    justify-content: center;
}

.step:last-child{
    width: 60px;
    max-width: 60px;
}

.step-line{
    width: 100%;
    height: 5px;
    background-color: var(--passive-color);
    top: 50%;
    left: 0;
    position: absolute;
    z-index: -1;
    transform: translateY(-50%);
}
.step:last-child .step-line{
    display: none;
}

.step-active .step-bubble,
.step-done .step-bubble{
    width: 60px;
    height: 60px;
    background-color: var(--active-color);
}

</style>