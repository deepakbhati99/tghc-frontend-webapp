<template>
    <div>
        <div class="h-100 bg-premium-dark">
            <div class="d-flex h-100 justify-content-center align-items-center">
                <b-col md="5" class="mx-auto app-login-box" >
                    <div class="app-logo-inverse mx-auto mb-3"/>

                    <div class=" w-100 mx-auto">
                        <b-row>
                        <b-col md="12">
                            <b-card title="" class="main-card mb-3">
                             <div class="modal-header">
                                    <div class="h5 modal-title" >
                                        <h3 style="font-weight:bold">Login </h3>
                                    </div>
                                </div>
                            <center>
                                <b-form @submit="onSubmit">
                                <v-flex xs12 md8 >
                                <v-text-field
                                    v-model="email"
                                    :rules="emailRules"
                                    label="E-mail"
                                    required
                                ></v-text-field>
                                </v-flex>




                                <v-flex xs12 md8 >
                                <v-text-field
                                    v-model="password"
                                    :rules="passwordRules"
                                    label="Password"
                                    type="password"
                                    required
                                ></v-text-field>
                                </v-flex>
                            
                                <br>
                                <br>

                                <v-btn color="normal"  type="submit" class="pull-left" dark> <i class="lnr-lock icon-gradient bg-malibu-beach"> </i> &nbsp; Login</v-btn>
                    
                            </b-form>
                            </center>
                                <v-btn color="primary" class="pull-left" @click="signup()" dark>Sign Up</v-btn>
                                <v-btn color="error" class="pull-right" @click="forgot()" dark>Forgot Password</v-btn>
                            </b-card>
                        </b-col>
                        </b-row>
                    </div>
                    
                </b-col>
            </div>
        </div>
    </div>
</template>
<script>

  import PageTitle from "../PageTitle.vue";
  import Tabs from 'vue-tabs-with-active-line';
  import { validationMixin } from "vuelidate"
  import { required, minLength } from "vuelidate/lib/validators"

  const TABS = [{
    title: 'Advanced',
    value: 'tab1',
  }, {
    title: 'Feedback',
    value: 'tab2',
  }];

  export default {
    components: {
      PageTitle,
      Tabs,
    },
    data: () => ({
      heading: 'Form Validation',
      subheading: 'Inline validation is very easy to implement using the ArchitectUI Framework.',
      icon: 'lnr-picture text-danger',

      tabs: TABS,

      passwordRules: [
        v => !!v || 'Password is required',
      ],
      email: '',
      emailRules: [
        v => !!v || 'E-mail is required',
        v => /.+@.+/.test(v) || 'E-mail must be valid'
      ],

   
      form: {}
    }),
   
 
    methods: {
      handleClick(newTab) {
        this.currentTab = newTab;
      },

      onSubmit() {
        // alert("0");dashboards/analytics
             this.$router.push('/dashboards/analytics'); 
      },

      signup(){
      this.$router.push('/pages/register'); 
      },

      forgot(){
      this.$router.push('/pages/forgot-password'); 
      }
    }
  }
</script>
<style>
.h-100 {
    height: 100vh !important;
}
.bg-malibu-beach {
    background-image: linear-gradient(to right, #ffffff 0%, #ffffff 100%) !important;
}

.modal-title{
  text-align: center;
}
.app-logo-inverse {
    height: 70px;
    width: 70px;
    background-size: cover;
    }
</style>