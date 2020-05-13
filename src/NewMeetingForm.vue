<template>
    <form @submit.prevent="addNewMeeting()">
            <h3>Dodaj nowe spotkanie</h3>
            <label>Nazwa</label>
            <input type="text" v-model="newMeeting.name">
            <label>Opis</label>
            <textarea v-model="newMeeting.description"></textarea>
            <button >Dodaj</button>
            <p>{{error}}</p>
        </form>
</template>

<script>
export default {
  data() {
      return {
          newMeeting: {},
          error: '',
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
    	  }    
    }
  }
}
</script>