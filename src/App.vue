<template>
  <div class="wrapper">
    <div class="wrapper-content">

      <section>
        <div class="container">

          <message v-if="message" :message="message"/>

          <newNote :note="note" @addNote="addNote"/>
          
					<div class="note-header">
						<h1>{{ title }}</h1>
							<div class="icons">
								<svg :class="{ active: grid }" @click="grid = true" xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round" ><rect x="3" y="3" width="7" height="7"></rect><rect x="14" y="3" width="7" height="7"></rect><rect x="14" y="14" width="7" height="7"></rect><rect x="3" y="14" width="7" height="7"></rect></svg>
								<svg :class="{ active: !grid }" @click="grid = false" xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"><line x1="8" y1="6" x2="21" y2="6"></line><line x1="8" y1="12" x2="21" y2="12"></line><line x1="8" y1="18" x2="21" y2="18"></line><line x1="3" y1="6" x2="3" y2="6"></line><line x1="3" y1="12" x2="3" y2="12"></line><line x1="3" y1="18" x2="3" y2="18"></line></svg>
							</div>
					</div>

          <!-- note list -->
					<notes :notes="notes" :grid="grid" @remove="removeNote"/>
					

        </div>
      </section>

    </div> 
  </div>
</template>

<script>
import message from '@/components/Message.vue'
import newNote from '@/components/NewNote.vue'
import notes from '@/components/Notes.vue'

export default {
  components: {
    message, newNote, notes
  },
  data () {
    return {
      title: 'Notes App',
			message: null,
			grid: true,
			note: {
				title: '',
				descr: ''
			},
			notes: [
				{
					title: 'First Note',
					descr: 'Description for first note',
					date: new Date(Date.now()).toLocaleString()
				},
				{
					title: 'Second Note',
					descr: 'Description for second note',
					date: new Date(Date.now()).toLocaleString()
				},
				{
					title: 'Third Note',
					descr: 'Description for third note',
					date: new Date(Date.now()).toLocaleString()
				}
			]
    }
  },
  methods: {
			addNote () {
				// console.log(this.note)
				let {title, descr} = this.note

				if (title === '') {
					this.message = 'title cant be blank!'
					return false
				}

				this.notes.push({
					title,
					descr,
					date: new Date(Date.now()).toLocaleString()
				})
				this.message = null
				this.note.title = ''
				this.note.descr = ''
			},
			removeNote (index) {
				this.notes.splice(index, 1)
			}
		}
}
</script>


<style lang="scss">

.note-header {
		display: flex;
		align-items: center;
		justify-content: space-between;
}
	h1 {
		font-size: 32px;
	}
	svg {
		cursor: pointer;
		margin-right: 10px; 
		color: #999999;
		&.active {
			color: #5524a5;
		}
	
		&:last-child {
			margin-right: 0;
		}
	&.full{
		width: 100%;
		text-align: center;
		justify-content: center;
		p{
			margin-right: 15px;
			&:last-child{
				margin-right: 0;
			}
		}
	}	
	}


</style>
