<template>
  <v-container>
      <v-navigation-drawer
        v-model="drawer"
        absolute
        clipped
        right
      >
      <template v-slot:prepend>
        <v-list-item two-line>
          <v-list-item-avatar>
            <img src="https://randomuser.me/api/portraits/women/81.jpg">
          </v-list-item-avatar>

          <v-list-item-content>
            <v-list-item-title>Jane Smith</v-list-item-title>
            <v-list-item-subtitle>Logged In</v-list-item-subtitle>
          </v-list-item-content>
        </v-list-item>
      </template>
      <v-divider></v-divider>
      </v-navigation-drawer>
    <v-card max-width="344" class="mx-auto">
      <v-list-item>
        <v-list-item-content>
          <v-list-item-title class="headline">My Events List</v-list-item-title>
        </v-list-item-content>
        <v-list-item-icon>
          <v-icon>mdi-calendar </v-icon>
        </v-list-item-icon>
      </v-list-item>
      <v-list-item-group color="primary" class="list-events" v-model="model">
        <template v-for="(event, index) in events">
          <v-divider :key="index"></v-divider>
          <v-list-item :key="event.eventId" three-line @click="openEventDrawer(event.eventId)">
            <v-list-item-content>
              <v-list-item-title v-text="event.eventTitle"></v-list-item-title>
              <v-list-item-avatar color="red" class="user-avatar">
                <span class="white--text headline">CJ</span>
              </v-list-item-avatar>
                <v-list-item class="event-details">
                  <v-list-item-icon>
                    <v-icon>mdi-calendar-range</v-icon>
                  </v-list-item-icon>
                  <v-list-item-subtitle v-text="getEventDate(event.start)"></v-list-item-subtitle>
                </v-list-item>
                <v-list-item class="event-details">
                  <v-list-item-icon>
                    <v-icon>mdi-clock</v-icon>
                  </v-list-item-icon>
                  <v-list-item-subtitle
                    v-text="getEventTime(event.start, event.end)"
                  >
                  </v-list-item-subtitle>
                </v-list-item>
                <v-list-item class="event-details">
                  <v-list-item-icon>
                    <v-icon>mdi-map-marker</v-icon>
                  </v-list-item-icon>
                  <v-list-item-subtitle v-text="event.location"></v-list-item-subtitle>
                </v-list-item>
              <v-list-item-subtitle v-text="event.description"></v-list-item-subtitle>
            </v-list-item-content>
          </v-list-item>
        </template>
      </v-list-item-group>
    </v-card>
  </v-container>
</template>

<script>
export default {
  name: 'HomePage',
  data() {
    return {
      drawer: false,
      model: Number,
      item: 1,
      eventds: [
        { title: 'Home', icon: 'mdi-home-city' },
        { title: 'My Account', icon: 'mdi-account' },
        { title: 'Users', icon: 'mdi-account-group-outline' },
      ],
      events: [
        {
          eventId: 54,
          eventTitle: 'Birthday',
          start: '2015-03-25T12:00:00Z',
          end: '2015-03-25T16:00:00Z',
          location: 'Room A',
          description: 'birthday celeberation of thendi pattiLorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry\'s standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book.',
        },
        {
          eventId: 454,
          eventTitle: 'Marriage',
          start: '2015-03-25T17:00:00Z',
          end: '2015-03-25T18:00:00Z',
          location: 'Room B',
          description: 'Marriage celeberation of thendi patti Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry\'s standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book.',
        },
        {
          eventId: 4545,
          eventTitle: 'Funeral',
          start: '2015-03-25T19:00:00Z',
          end: '2015-03-25T20:00:00Z',
          location: 'Room C',
          description: 'Funeral celeberation of thendi patti Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry\'s standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book.',
        },
        {
          eventId: 4343545,
          eventTitle: 'Funeral',
          start: '2015-03-25T19:00:00Z',
          end: '2015-03-25T20:00:00Z',
          location: 'Room C',
          description: 'Funeral celeberation of thendi patti Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry\'s standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book.',
        },
        {
          eventId: 435,
          eventTitle: 'Funeral',
          start: '2015-03-25T19:00:00Z',
          end: '2015-03-25T20:00:00Z',
          location: 'Room C',
          description: 'Funeral celeberation of thendi patti Lorem Ipsum is simply dummy text of the printing and typesetting industry. Lorem Ipsum has been the industry\'s standard dummy text ever since the 1500s, when an unknown printer took a galley of type and scrambled it to make a type specimen book.',
        },
      ],
    };
  },
  methods: {
    getEventDate(date) {
      const d = new Date(date);
      return d.toDateString();
    },
    getEventTime(start, end) {
      const s = new Date(start);
      const e = new Date(end);
      return `${s.toLocaleTimeString('en-US')} - ${e.toLocaleTimeString('en-US')}`;
    },
    openEventDrawer(index) {
      console.log(`sd${index}`);
      console.log(this.model);
      if (this.drawer === false) {
        this.drawer = true;
      }
    },
  },
};
</script>

<style scoped>
.event-details {
  padding: 0;
  height: 32px !important;
  min-height: 32px !important;
  left: 90px;
  pointer-events: none;
}
/* Icons next to event details */
.event-details .v-list-item__icon {
  margin-top: 2px;
  margin-right: 12px !important;
}
/* v-list-item-group that contains all the events*/
.list-events {
  height: 460px;
  overflow-y: auto;
}
.user-avatar {
  height: 60px !important;
  min-width: 60px !important;
  width: 60px !important;
  left: 30px;
  top: 35px;
  position: absolute;
}
</style>
