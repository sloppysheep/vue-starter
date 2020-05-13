<template>
<div>
    <form v-if="formOn" @submit.prevent="addNewMeeting()">
            <h3>Dodaj nowe spotkanie</h3>
            <label>Nazwa</label>
            <input type="text" v-model="newMeeting.name">
            <label>Opis</label>
            <textarea v-model="newMeeting.description"></textarea>
            <button>Dodaj</button> 
            <nobr style="color:rgb(246,70,90)" margin-left:10px> {{error}}</nobr>
    </form>
    <button v-if="!formOn" @click="showForm()">Dodaj nowe spotkanie</button> 
</div>
</template>

<script>
export default {
  data() {
      return {
          newMeeting: {},
          error: '',
          formOn: false
      };
  },
  
  methods: {
      addNewMeeting() {
    	  if(this.newMeeting.name==null) {
    		  this.error = 'Spotkanie musi mieć nazwę!';
    	  }
    	  else {
    	        this.$emit('added', this.newMeeting);
    	    	this.newMeeting = {};
    	    	this.error = '';
    	    	this.formOn = false;
    	  }    
      },
      showForm() {this.formOn = true;}
  }
}
</script>
