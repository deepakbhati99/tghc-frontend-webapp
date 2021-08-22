<template>
  <div>
    <b-row>
      <b-col md="8">
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
              Members List
            </b-col>
            <b-col class="btn-actions-pane-right font-weight-bold" md="6">
              <v-select multiple :options="options2" v-model="selected2"></v-select>
            </b-col>


          </div>
          <b-card class="main-card">
               <table class="table table-striped">
              <thead>
                <tr>
                  <th>Name</th>
                  <th>Patient Id</th>
                  <th>Health Condition</th>
                  <th>Member Since Date</th>
                  <th>Missed Calls</th>
                  <th>Unread Messages</th>
                  <th>Calls For Today</th>
                  <th>Next Paln Due Date</th>
                  <th>Points Yesterday</th>
                </tr>
              </thead>
              <tbody>
                <tr v-for="item in memberlist" :key="item">
                  <td>{{item.name}}</td>
                  <td>{{item.patient_id}}</td>
                  <td>{{item.health_condition}}</td>
                  <td>{{item.member_since_date}}</td>
                  <td>{{item.missed_calls}}</td>
                  <td> {{item.unread_messages}}</td>
                  <td>{{item.calls_for_today}}</td>
                  <td>{{item.next_paln_due_date}}</td>
                  <td>{{item.points_yesterday}}</td>
                </tr>
                
              </tbody>
            </table>
            <div class="card-footer-tab card-footer">
              <b-col colmd="6">
                <button class="mr-2 btn-shadow btn-sm btn btn-dark">
                  <font-awesome-icon icon="plus" /> New Member
                </button>
              </b-col>
              <b-col md="6">
                <v-pagination
                  v-model="salescallspage"
                  :length="4"
                ></v-pagination>
              </b-col>
            </div>
          </b-card>
        </b-col>
      </b-col>

      <b-col md="4">
        <b-col md="12">
            <b-card class="main-card">
           <v-date-picker v-model='date' mode="date" />
          </b-card>

        </b-col>
        <b-col md="12">
          <div class="card-header-tab card-header">
            <div
              class="
                card-header-title
                font-size-lg
                text-capitalize
                font-weight-bold
              "
            >
              Today
            </div>
            <div class="btn-actions-pane-right actions-icon-btn">
              <button class="mr-2 btn-shadow btn-sm btn btn-dark">
                <font-awesome-icon icon="plus" /> New Schedule
              </button>
            </div>
          </div>
        </b-col>
        <b-col md="12">
          <b-card>
            <ul class="list-group" v-for="item in scheduleitems" :key="item">
              <li class="list-group-item">
                <h6 class="font-weight-bold">{{ item.title }}</h6>
                <div class="f12">
                  <span class="pull-left">{{ item.subtitle }}</span>
                  <span class="pull-right">{{ item.time }}</span>
                </div>
              </li>
            </ul>
          </b-card>
        </b-col>
      </b-col>
    </b-row>

    &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;
    <b-row>
      <b-col md="7" style="float: left">
        <b-col md="12" style="float: left">
          <div class="card-header-tab card-header">
            <div
              class="
                card-header-title
                font-size-lg
                text-capitalize
                font-weight-bold
              "
            >
              Sales Calls
            </div>
          </div>

          <b-card class="mb-3 nav-justified">
            <table class="table table-striped">
              <thead>
                <tr>
                  <th>Time Slot</th>
                  <th>Name</th>
                  <th>Mobile</th>
                  <th>Email</th>
                  <th>Place</th>
                </tr>
              </thead>
              <tbody>
                <tr>
                  <td rowspan="2"><font-awesome-icon icon="calendar-alt" />&nbsp; 10:05 AM</td>
                  <td>John</td>
                  <td>9998885556</td>
                  <td>john@gmail.com</td>
                  <td>India</td>
                </tr>
                <tr style="padding: 0%">
                  <td colspan="4" style="padding: 0%">
                    <span class="mr-2 badge badge-success">Accept</span>
                    <span class="mr-2 badge badge-danger">Reject</span>
                    <span class="mr-2 badge badge-dark">Reschedule</span>
                  </td>
                </tr>

                <tr>
                  <td rowspan="2"><font-awesome-icon icon="calendar-alt" />&nbsp;11:00 AM</td>
                  <td>Lucy</td>
                  <td>999877755</td>
                  <td>lucy@gmail.com</td>
                  <td>UK</td>
                </tr>
                <tr style="padding: 0%">
                  <td colspan="4" style="padding: 0%">
                    <span class="mr-2 badge badge-success">Accept</span>
                    <span class="mr-2 badge badge-danger">Reject</span>
                    <span class="mr-2 badge badge-dark">Reschedule</span>
                  </td>
                </tr>
              </tbody>
            </table>

            <hr />
            <div class="text-xs-center mb-3">
              <v-pagination v-model="salescallspage" :length="4"></v-pagination>
            </div>
          </b-card>
        </b-col>

        <b-col md="12" style="float: left">
          <div class="card-header-tab card-header">
            <div
              class="
                card-header-title
                font-size-lg
                text-capitalize
                font-weight-bold
              "
            >
              Latest Updates
            </div>
            <div class="btn-actions-pane-right actions-icon-btn">
              <button class="mr-2 btn-shadow btn-sm btn btn-dark"  @click="createblog()">
                <font-awesome-icon icon="plus" /> Create Blog
              </button>
              &nbsp; &nbsp;
              <button class="mr-2 btn-shadow btn-sm btn btn-dark"  @click="createvideo()">
                <font-awesome-icon icon="plus" /> Create Video
              </button>
            </div>
          </div>

          <b-card class="mb-3 nav-justified" no-body>
            <b-tabs card>
              <b-tab title="Blog" active>
                <b-col
                  md="3"
                  v-for="item in blogs"
                  :key="item"
                  style="float: left"
                >
                  <img
                    src="@/assets/images/avatars/2.jpg"
                    alt=""
                    hwight="100px"
                    width="100px;"
                  />
                  <br />
                  <p class="card-header-title font-size-md">{{ item.title }}</p>
                </b-col>
              </b-tab>
              <b-tab title="Video">
                <b-col
                  md="3"
                  v-for="item in blogs"
                  :key="item"
                  style="float: left"
                >
                  <img
                    src="@/assets/images/avatars/3.jpg"
                    alt=""
                    hwight="100px"
                    width="100px;"
                  />
                  <br />
                  <p class="card-header-title font-size-md">{{ item.title }}</p>
                </b-col>
              </b-tab>
            </b-tabs>
          </b-card>
        </b-col>
      </b-col>

      <b-col md="5" style="float: left">
        <b-col
          md="12"
          class="app-inner-layout__content card"
          style="float: left"
        >
          <div class="card-header-tab card-header">
            <div
              class="
                card-header-title
                font-size-lg
                text-capitalize
                font-weight-bold
              "
            >
              Chat Manager
            </div>
            <div class="btn-actions-pane-right font-weight-bold">
              <i class="pe-7s-search fa-2x"></i>
            </div>
          </div>
        </b-col>

        <b-col
          md="6"
          class="app-inner-layout__content card"
          style="float: left"
        >
          <div class="app-inner-layout__sidebar card">
            <ul class="nav flex-column">
              <li class="nav-item">
                <button type="button" tabindex="0" class="dropdown-item">
                  <div class="widget-content p-0">
                    <div class="widget-content-wrapper">
                      <div class="widget-content-left mr-3">
                        <div class="avatar-icon-wrapper">
                          <div
                            class="
                              badge
                              badge-bottom
                              badge-success
                              badge-dot
                              badge-dot-lg
                            "
                          ></div>
                          <div class="avatar-icon">
                            <img src="@/assets/images/avatars/2.jpg" alt="" />
                          </div>
                        </div>
                      </div>
                      <div class="widget-content-left">
                        <div class="widget-heading">Alina Mcloughlin</div>
                        <div class="widget-subheading">
                          Last meet at 15:00PM
                        </div>
                      </div>
                    </div>
                  </div>
                </button>
              </li>
              <li class="nav-item">
                <button type="button" tabindex="0" class="dropdown-item">
                  <div class="widget-content p-0">
                    <div class="widget-content-wrapper">
                      <div class="widget-content-left mr-3">
                        <div class="avatar-icon-wrapper">
                          <div
                            class="
                              badge
                              badge-bottom
                              badge-success
                              badge-dot
                              badge-dot-lg
                            "
                          ></div>
                          <div class="avatar-icon">
                            <img src="@/assets/images/avatars/3.jpg" alt="" />
                          </div>
                        </div>
                      </div>
                      <div class="widget-content-left">
                        <div class="widget-heading">Chad Evans</div>
                        <div class="widget-subheading">
                          Last meet at 15:00PM
                        </div>
                      </div>
                    </div>
                  </div>
                </button>
              </li>
              <li class="nav-item">
                <button type="button" tabindex="0" class="dropdown-item">
                  <div class="widget-content p-0">
                    <div class="widget-content-wrapper">
                      <div class="widget-content-left mr-3">
                        <div class="avatar-icon-wrapper">
                          <div
                            class="
                              badge
                              badge-bottom
                              badge-success
                              badge-dot
                              badge-dot-lg
                            "
                          ></div>
                          <div class="avatar-icon">
                            <img src="@/assets/images/avatars/3.jpg" alt="" />
                          </div>
                        </div>
                      </div>
                      <div class="widget-content-left">
                        <div class="widget-heading">Ella-Rose Henry</div>
                        <div class="widget-subheading">
                          Last meet at 15:00PM
                        </div>
                      </div>
                    </div>
                  </div>
                </button>
              </li>
              <li class="nav-item">
                <button type="button" tabindex="0" class="dropdown-item">
                  <div class="widget-content p-0">
                    <div class="widget-content-wrapper">
                      <div class="widget-content-left mr-3">
                        <div class="avatar-icon-wrapper">
                          <div
                            class="
                              badge
                              badge-bottom
                              badge-success
                              badge-dot
                              badge-dot-lg
                            "
                          ></div>
                          <div class="avatar-icon">
                            <img src="@/assets/images/avatars/2.jpg" alt="" />
                          </div>
                        </div>
                      </div>
                      <div class="widget-content-left">
                        <div class="widget-heading">Ruben Tillman</div>
                        <div class="widget-subheading">
                          Last meet at 15:00PM
                        </div>
                      </div>
                    </div>
                  </div>
                </button>
              </li>
              <li class="nav-item">
                <button type="button" tabindex="0" class="dropdown-item">
                  <div class="widget-content p-0">
                    <div class="widget-content-wrapper">
                      <div class="widget-content-left mr-3">
                        <div class="avatar-icon-wrapper">
                          <div
                            class="
                              badge
                              badge-bottom
                              badge-success
                              badge-dot
                              badge-dot-lg
                            "
                          ></div>
                          <div class="avatar-icon">
                            <img src="@/assets/images/avatars/3.jpg" alt="" />
                          </div>
                        </div>
                      </div>
                      <div class="widget-content-left">
                        <div class="widget-heading">Ella-Rose Henry</div>
                        <div class="widget-subheading">
                          Last meet at 15:00PM
                        </div>
                      </div>
                    </div>
                  </div>
                </button>
              </li>
              <li class="nav-item">
                <button type="button" tabindex="0" class="dropdown-item">
                  <div class="widget-content p-0">
                    <div class="widget-content-wrapper">
                      <div class="widget-content-left mr-3">
                        <div class="avatar-icon-wrapper">
                          <div
                            class="
                              badge
                              badge-bottom
                              badge-success
                              badge-dot
                              badge-dot-lg
                            "
                          ></div>
                          <div class="avatar-icon">
                            <img src="@/assets/images/avatars/2.jpg" alt="" />
                          </div>
                        </div>
                      </div>
                      <div class="widget-content-left">
                        <div class="widget-heading">Ruben Tillman</div>
                        <div class="widget-subheading">
                          Last meet at 15:00PM
                        </div>
                      </div>
                    </div>
                  </div>
                </button>
              </li>
            </ul>
          </div>
        </b-col>

        <b-col
          md="6"
          class="app-inner-layout__content card"
          style="float: left"
        >
          <div class="table-responsive">
            <div class="app-inner-layout__top-pane">
              <div class="pane-left">
                <div class="mobile-app-menu-btn">
                  <button
                    type="button"
                    class="hamburger hamburger--elastic"
                    v-bind:class="{ 'is-active': isMobileOpen }"
                    @click="toggleLayoutClass('open-mobile-menu')"
                  >
                    <span class="hamburger-box">
                      <span class="hamburger-inner"></span>
                    </span>
                  </button>
                </div>
                <div class="avatar-icon-wrapper">
                  <div
                    class="
                      badge badge-bottom
                      btn-shine
                      badge-success badge-dot badge-dot-lg
                    "
                  ></div>
                  <div class="avatar-icon ">
                    <img
                      width="82"
                      src="@/assets/images/avatars/1.jpg"
                      alt=""
                    />
                  </div>
                </div>
                <h6 class="mb-0 text-nowrap">
                  Chad Evans
                  <div class="opacity-7">
                    Last Seen Online:
                    <span class="opacity-8">10 minutes ago</span>
                  </div>
                </h6>
              </div>
            </div>
  
            <div class="chat-wrapper">
              <div class="chat-box-wrapper">
                <div>
                  <div class="avatar-icon-wrapper mr-1">
                    <div
                      class="
                        badge badge-bottom
                        btn-shine
                        badge-success badge-dot badge-dot-lg
                      "
                    ></div>
                    <div class="avatar-icon avatar-icon-lg rounded">
                      <img src="@/assets/images/avatars/2.jpg" alt="" />
                    </div>
                  </div>
                </div>
                <div>
                  <div class="chat-box">But I must explain to you how al.</div>
                  <small class="opacity-6">
                    <font-awesome-icon icon="calendar-alt" />
                    11:01 AM | Yesterday
                  </small>
                </div>
              </div>
              <div class="float-right">
                <div class="chat-box-wrapper chat-box-wrapper-right">
                  <div>
                    <div class="chat-box">Expound the actual teachi.</div>
                    <small class="opacity-6">
                      <font-awesome-icon icon="calendar-alt" />
                      11:01 AM | Yesterday
                    </small>
                  </div>
                  <div>
                    <div class="avatar-icon-wrapper ml-1">
                      <div
                        class="
                          badge badge-bottom
                          btn-shine
                          badge-success badge-dot badge-dot-lg
                        "
                      ></div>
                      <div class="avatar-icon avatar-icon-lg rounded">
                        <img src="@/assets/images/avatars/2.jpg" alt="" />
                      </div>
                    </div>
                  </div>
                </div>
              </div>
              <div class="chat-box-wrapper">
                <div>
                  <div class="avatar-icon-wrapper mr-1">
                    <div
                      class="
                        badge badge-bottom
                        btn-shine
                        badge-success badge-dot badge-dot-lg
                      "
                    ></div>
                    <div class="avatar-icon avatar-icon-lg rounded">
                      <img src="@/assets/images/avatars/2.jpg" alt="" />
                    </div>
                  </div>
                </div>
                <div>
                  <div class="chat-box">
                    But I must explain to you how all this mistaken idea of deno
                  </div>
                  <small class="opacity-6">
                    <font-awesome-icon icon="calendar-alt" />
                    11:01 AM | Yesterday
                  </small>
                </div>
              </div>

              <div class="chat-box-wrapper">
                <div>
                  <div class="avatar-icon-wrapper mr-1">
                    <div
                      class="
                        badge badge-bottom
                        btn-shine
                        badge-success badge-dot badge-dot-lg
                      "
                    ></div>
                    <div class="avatar-icon avatar-icon-lg rounded">
                      <img src="@/assets/images/avatars/2.jpg" alt="" />
                    </div>
                  </div>
                </div>
                <div>
                  <div class="chat-box">
                    Mistaken idea of denouncing pleasure
                  </div>
                  <small class="opacity-6">
                    <font-awesome-icon icon="calendar-alt" />
                    11:01 AM | Yesterday
                  </small>
                </div>
              </div>
            </div>
            <div class="app-inner-layout__bottom-pane d-block text-center">
              <div class="mb-0 position-relative row form-group">
                <div class="col-sm-12">
                  <input
                    placeholder="Write here..."
                    type="text"
                    class="form-control-md form-control"
                  />
                </div>
              </div>
            </div>
          </div>
        </b-col>
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

  methods: {

      createblog(){
      this.$router.push('/coach/create-blog'); 
      },
       createvideo(){
      this.$router.push('/coach/create-video'); 
      }
  },
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


.chat-box-wrapper .chat-box {
  font-size: 11px;
    -webkit-box-shadow: 0 0 0 transparent;
    box-shadow: 0 0 0 transparent;
    position: relative;
    opacity: 1;
    background: #e0f3ff;
    border: 0;
    padding: 0.55rem 1rem;
    border-radius: 30px;
    border-top-left-radius: 0.25rem;
    -webkit-box-flex: 1;
    -ms-flex: 1;
    flex: 1;
    display: -webkit-box;
    display: -ms-flexbox;
    display: flex;
    max-width: 50%;
    min-width: 100%;
    text-align: left;
}

.v-select .vs__selected-options {
    font-size: 12px;
    display: flex;
    flex-basis: 100%;
    flex-grow: 1;
    flex-wrap: wrap;
    padding: 0 1px;
    position: relative;
}
.v-select .selected-tag {
    font-size: 12px;
    display: flex;
    align-items: center;
    background-color: #f0f0f0;
    border: 1px solid #ccc;
    border-radius: 4px;
    color: #333;
    line-height: 1.0;
    margin: 4px 2px 0;
    padding: 0 .25em;
    transition: opacity .25s;
}
.opacity-7, .opacity-8{
  font-size: 11px;
}
.app-inner-layout__top-pane{
  min-height: 50px;
  border-bottom: 2px #bbb solid;
  padding: 5px;
}
 .chat-wrapper{
  max-height: 260px;
  min-height: 260px;
    overflow: scroll;
}
.app-inner-layout__sidebar{
  max-height: 400px;
  min-height: 400px;
}


</style>