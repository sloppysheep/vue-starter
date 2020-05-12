<template>
<div>
	<new-meeting-form @added="addNewMeeting($event)"></new-meeting-form>
	<div v-if="meetings.length !==0">
		<h3>Zaplanowane zajęcia ({{meetings.length}})</h3>
		<meetings-list :meetings="meetings" :username="username"
			@signup="signUp($event)" @signout="signOut($event)"
			@removed=removeMeeting($event)></meetings-list>
	</div>
	<div v-else>
		<p>Brak zaplanowanych spotkań</p>
	</div>


</div>
</template>

<script>
import NewMeetingForm from "./NewMeetingForm";
import MeetingsList from "./MeetingsList";

export default {
  props: ['username'],
  components: {NewMeetingForm, MeetingsList},
  data() {
      return {
          meetings: []
      };
  },
  methods: {
/*        addNewMeeting(meeting) {
          this.meetings.push(meeting);
      },  */
       addNewMeeting(meeting) {
          this.meetings.push({...meeting, participants: []});
      }, 
       removeMeeting(meeting) {
    	  this.meetings = this.meetings.filter(item => item !== meeting);
      }, 
      signUp(meeting) {
    	  this.meetings.find(item => item === meeting).participants.push(this.username);
      },
       signOut(meeting) {
    	   this.meetings.find(item => item === meeting).participants = this.meetings.find(item => item === meeting).participants.filter(item => item !== this.username);
      }      
  }
}
</script>