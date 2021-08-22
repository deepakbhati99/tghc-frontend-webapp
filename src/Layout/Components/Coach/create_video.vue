<template>
  <div>
    <b-row>
           <b-col md="12" style="float: left">
           <div class="card-header-tab card-header">
            <b-col md="6"
              class="
                card-header-title
                font-size-lg
                text-capitalize
                font-weight-bold
              "
            >
              Create Video
            </b-col>
            <b-col class="btn-actions-pane-right font-weight-bold" md="6">
             
            </b-col>


          </div>
          <b-card class="main-card">
                  <form class="">
                                <div class="form-row">
                                <div class="col-md-6">
                                    <div class="position-relative form-group"><label for="firstname" class="">Select Video</label><input name="video" id="video"  type="file" class="form-control"></div>
                                </div>
                        
                                </div>


                                <div class="form-row">
                                    <div class="col-md-6">
                                        <div class="position-relative form-group"><label for="lastname" class="">Video Title</label><input name="title" id="title" placeholder="Title" type="text" class="form-control"></div>
                                    </div>                         
                                </div>

                      
                                
                                <div class="modal-footer d-block text-center">
                               <button class="btn-shadow btn-md btn btn-dark ">
                                    <font-awesome-icon icon="save" /> Save
                                </button>
                            </div>
                            </form>
            <div class="card-footer-tab card-footer"></div>
          </b-card>
        </b-col>
  

    
    </b-row>

  </div>
</template>

<script>
import PageTitle from "..//PageTitle.vue";
import VueCircle from "vue2-circle-progress";
import VuePerfectScrollbar from "vue-perfect-scrollbar";
import { FullCalendar } from "vue-full-calendar";
import Calendar from 'v-calendar/lib/components/calendar.umd'
import DatePicker from 'v-calendar/lib/components/date-picker.umd'
  import vSelect from 'vue-select'
  import Multiselect from 'vue-multiselect'
import { library } from "@fortawesome/fontawesome-svg-core";
import {
  faCalendarAlt,
  faSave,
  faAngleDown,
  faStar,
  faAngleUp,
  faTh,
  faBusinessTime,
  faArrowLeft,
  faArrowRight,
  faCog,
  faDotCircle,
} from "@fortawesome/free-solid-svg-icons";
import { FontAwesomeIcon } from "@fortawesome/vue-fontawesome";

library.add(
  faAngleDown,
  faCalendarAlt,
  faSave,
  faStar,
  faAngleUp,
  faTh,
  faBusinessTime,
  faCog,
  faArrowLeft,
  faArrowRight,
  faDotCircle
);

export default {
  data() {
    
    return {
      date: new Date(),
      memberpage: 1,
      salescallspage: 1,
    };
  },
  components: {
    PageTitle,
    VueCircle,
    VuePerfectScrollbar,
    FullCalendar,
    Calendar,
    DatePicker,    
    'v-select': vSelect,
      Multiselect,
    "font-awesome-icon": FontAwesomeIcon,
  },

  data: () => ({
    heading: "Gauges",
    subheading:
      "Create wonderful animated gauges that can be used in combination with other ArchitectUI elements.",
    icon: "pe-7s-car icon-gradient bg-warm-flame",

    fill: { gradient: ["var(--primary)"] },
    fill1: { gradient: ["#2af598", "#009efd"] },
    fill2: { gradient: ["#fccb90", "#d57eeb"] },

    f1: { gradient: ["#3f6ad8"] },
    f2: { gradient: ["#3ac47d"] },
    f3: { gradient: ["#16aaff"] },
    f4: { gradient: ["#f7b924"] },
    f5: { gradient: ["#d92550"] },
    f6: { gradient: ["#444054"] },

      selected2: [],
      options2: ['Name', 'Patient Id', 'Health Condition', 'Member Since Date', 'Missed Calls', 'Unread Messages', 'Calls For Today', 'Next Paln Due Date', 'Points Yesterday'],


   
      

    memberlist: [
      {
        name: "Dickerson",
        patient_id: 101,
        health_condition: "Anxiety",
        member_since_date: "05-09-2016",
        missed_calls: "4 Calls",
        unread_messages: "2",
        calls_for_today: "1 Call 10:00",
        next_paln_due_date: "05-09-2021",
        points_yesterday: "105",
      },
      {
        name: "Dickerson",
        patient_id: 101,
        health_condition: "Anxiety",
        member_since_date: "05-09-2016",
        missed_calls: "4 Calls",
        unread_messages: "2",
        calls_for_today: "1 Call 10:00",
        next_paln_due_date: "05-09-2021",
        points_yesterday: "105",
      },
      {
        name: "Dickerson",
        patient_id: 101,
        health_condition: "Anxiety",
        member_since_date: "05-09-2016",
        missed_calls: "4 Calls",
        unread_messages: "2",
        calls_for_today: "1 Call 10:00",
        next_paln_due_date: "05-09-2021",
        points_yesterday: "105",
      },
      {
        name: "Dickerson",
        patient_id: 101,
        health_condition: "Anxiety",
        member_since_date: "05-09-2016",
        missed_calls: "4 Calls",
        unread_messages: "2",
        calls_for_today: "1 Call 10:00",
        next_paln_due_date: "05-09-2021",
        points_yesterday: "105",
      },
      {
        name: "Dickerson",
        patient_id: 101,
        health_condition: "Anxiety",
        member_since_date: "05-09-2016",
        missed_calls: "4 Calls",
        unread_messages: "2",
        calls_for_today: "1 Call 10:00",
        next_paln_due_date: "05-09-2021",
        points_yesterday: "105",
      },
      {
        name: "Dickerson",
        patient_id: 101,
        health_condition: "Anxiety",
        member_since_date: "05-09-2016",
        missed_calls: "4 Calls",
        unread_messages: "2",
        calls_for_today: "1 Call 10:00",
        next_paln_due_date: "05-09-2021",
        points_yesterday: "105",
      },
      {
        name: "Dickerson",
        patient_id: 101,
        health_condition: "Anxiety",
        member_since_date: "05-09-2016",
        missed_calls: "4 Calls",
        unread_messages: "2",
        calls_for_today: "1 Call 10:00",
        next_paln_due_date: "05-09-2021",
        points_yesterday: "105",
      },
      {
        name: "Dickerson",
        patient_id: 101,
        health_condition: "Anxiety",
        member_since_date: "05-09-2016",
        missed_calls: "4 Calls",
        unread_messages: "2",
        calls_for_today: "1 Call 10:00",
        next_paln_due_date: "05-09-2021",
        points_yesterday: "105",
      },
      {
        name: "Dickerson",
        patient_id: 101,
        health_condition: "Anxiety",
        member_since_date: "05-09-2016",
        missed_calls: "4 Calls",
        unread_messages: "2",
        calls_for_today: "1 Call 10:00",
        next_paln_due_date: "05-09-2021",
        points_yesterday: "105",
      },
    ],

    scheduleitems: [
      {
        title: "Introduction with Virat",
        subtitle: "Blood Sugar, Weight",
        time: "10:30AM",
      },

      {
        title: "Followup Call with Suresh",
        subtitle: "Blood Sugar, Weight",
        time: "11:00AM",
      },
      {
        title: "Call with Rohit",
        subtitle: "Blood Sugar, Weight",
        time: "12:00AM",
      },
    ],

    blogs: [
      {
        image: "@/assets/images/avatars/2.jpg",
        title: "keep your diet intact",
      },
      { image: "@/assets/images/avatars/2.jpg", title: "10 steps to avoid" },
      {
        image: "@/assets/images/avatars/2.jpg",
        title: "how can you reduce tummy in 5 steps",
      },
      {
        image: "@/assets/images/avatars/2.jpg",
        title: "bankopne 2000 acounts",
      },
    ],

    striped: true,
    bordered: false,
    outlined: false,
    small: false,
    hover: false,
    dark: false,
    fixed: false,
    footClone: false,
  }),

  methods: {},
};
</script>


<style>
.col-1,
.col-2,
.col-3,
.col-4,
.col-5,
.col-6,
.col-7,
.col-8,
.col-9,
.col-10,
.col-11,
.col-12,
.col,
.col-auto,
.col-sm-1,
.col-sm-2,
.col-sm-3,
.col-sm-4,
.col-sm-5,
.col-sm-6,
.col-sm-7,
.col-sm-8,
.col-sm-9,
.col-sm-10,
.col-sm-11,
.col-sm-12,
.col-sm,
.col-sm-auto,
.col-md-1,
.col-md-2,
.col-md-3,
.col-md-4,
.col-md-5,
.col-md-6,
.col-md-7,
.col-md-8,
.col-md-9,
.col-md-10,
.col-md-11,
.col-md-12,
.col-md,
.col-md-auto,
.col-lg-1,
.col-lg-2,
.col-lg-3,
.col-lg-4,
.col-lg-5,
.col-lg-6,
.col-lg-7,
.col-lg-8,
.col-lg-9,
.col-lg-10,
.col-lg-11,
.col-lg-12,
.col-lg,
.col-lg-auto,
.col-xl-1,
.col-xl-2,
.col-xl-3,
.col-xl-4,
.col-xl-5,
.col-xl-6,
.col-xl-7,
.col-xl-8,
.col-xl-9,
.col-xl-10,
.col-xl-11,
.col-xl-12,
.col-xl,
.col-xl-auto {
  position: relative;
  width: 100%;
  padding-right: 5px;
  padding-left: 5px;
}

td {
  font-size: 12px;
}
thead {
  background: #ddd;
}
.f12,.widget-subheading{
  font-size: 12px;
}

.text-bold{
    font-weight: bold!important;
}


</style>