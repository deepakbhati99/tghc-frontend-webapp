<template>
    <div>
        <div class="h-100 bg-premium-dark">
            <div class="d-flex h-100 justify-content-center align-items-center">
                <b-col md="6" class="mx-auto app-login-box" >
                    <div class="app-logo-inverse mx-auto mb-3"/>

                    <div class=" w-100 mx-auto">
                          <div class="main-card mb-3 card">
                                <div class="modal-header">
                                    <div class="h5 modal-title">
                                        <h3 style="font-weight:bold">Sign Up</h3>
                                    </div>
                                </div>
                            <div class="card-body">
                    
                            <form class="">
                                <div class="form-row">
                                <div class="col-md-6">
                                    <div class="position-relative form-group"><label for="firstname" class="">First Name</label><input name="firstname" id="firstname" placeholder="First Name" type="text" class="form-control"></div>
                                </div>
                                <div class="col-md-6">
                                    <div class="position-relative form-group"><label for="lastname" class="">Lastname</label><input name="lastname" id="lastname" placeholder="Last Name" type="text" class="form-control"></div>
                                </div>
                                </div>


                                <div class="form-row">
                                <div class="col-md-6">
                                    <div class="position-relative form-group"><label for="exampleEmail11" class="">Email</label><input name="email" id="exampleEmail11" placeholder="Enter E-Mail" type="email" class="form-control"></div>
                                </div>
                                <div class="col-md-6">
                                    <div class="position-relative form-group"><label for="examplePassword11" class="">Password</label><input name="password" id="examplePassword11" placeholder="Enter Password" type="password" class="form-control"></div>
                                </div>
                                </div>


                                <div class="form-row">
                                <div class="col-md-6">
                                <div class="position-relative form-group"><label for="mobile" class="">Mobile</label><input name="mobile" id="mobile" placeholder="Enter Mobile" type="text" class="form-control"></div>
                                </div>
                                
                                </div>
                                
                                <div class="modal-footer d-block text-center">
                                <b-button color="primary" class="btn-wide btn-pill btn-shadow btn-hover-shine"
                                          size="lg">Create Account
                                </b-button>
                            </div>
                            </form>
                            </div>
                        </div>
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

   
      form: {}
    }),
    mixins: [
      validationMixin
    ],
    validations: {
      form: {
        password: {
          required,
          minLength: minLength(6)
        },
        name: {
          required,
          minLength: minLength(4)
        }
      }
    },
    methods: {
      handleClick(newTab) {
        this.currentTab = newTab;
      },

      onSubmit() {
        // alert("0");
      },

       signup(){
      this.$router.push('/signup'); 
      }
    }
  }
</script>
<style>
.h-100 {
    height: 100vh !important;
}
.app-logo-inverse {
    height: 70px;
    width: 70px;
    background-size: cover;
    }
</style>