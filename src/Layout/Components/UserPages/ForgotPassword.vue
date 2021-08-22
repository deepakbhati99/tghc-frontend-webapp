<template>
    <div>
        <div class="h-100 bg-premium-dark">
            <div class="d-flex h-100 justify-content-center align-items-center">
                <b-col md="5" class="mx-auto app-login-box" >
                    <div class="app-logo-inverse mx-auto mb-3"/>

                    <div class=" w-100 mx-auto">
                       <div class="modal-content">
                             <div class="modal-header">
                                    <div class="h5 modal-title">
                                        <h3 style="font-weight:bold">Forgot your Password?</h3>
                                        <h6 class="mt-1 mb-0 opacity-8"><span>Use the form below to recover it.</span></h6>
                                    </div>
                                </div>
                            <div class="modal-body">
                                <div>
                                    <Form>
                                        <b-row form>
                                            <b-col md="12">
                                                <b-form-group>
                                                    <Label for="exampleEmail">Email</Label>
                                                    <b-form-input type="email" name="email" id="exampleEmail"
                                                                  placeholder="Email here..."/>
                                                </b-form-group>
                                            </b-col>
                                        </b-row>
                                    </Form>
                                </div>
                                <div class="divider"/>
                                <h6 class="mb-0">
                                    <a href="#/pages/register" class="text-primary">Sign in existing account</a>
                                </h6>
                            </div>
                            <div class="modal-footer clearfix">
                                <div class="float-right">
                                    <b-button variant="primary" size="lg">Recover Password</b-button>
                                </div>
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
        // alert("0");
      },

      signup(){
      this.$router.push('/pages/register'); 
      },

      forgot(){
      this.$router.push('/users/forgot'); 
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
.app-logo-inverse {
    height: 70px;
    width: 70px;
    background-size: cover;
    }
</style>