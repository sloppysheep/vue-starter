<template>
    <div>
        <button @click="signMeUp()">{{buttonLabelToDisplay}}</button>
    </div>
</template>

<script>
    export default {
    	props: ['buttonLabel'],
        data() {
            return {
                email: '',
            }
        },
        methods: {
            enter() {
                this.$emit('login', this.email);
            }
        },
        computed: {
      	  buttonLabelToDisplay() {
     		 return this.buttonLabel || 'Zaloguj się';  
    		}
      	}
    }
</script>