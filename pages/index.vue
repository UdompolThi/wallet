<template>
  <div class="container-fluid">
      <div class="row bg-title">
          <div class="col-lg-3 col-md-4 col-sm-4 col-xs-12">
              <h4 class="page-title">Dashboard</h4>
          </div>
      </div>
      <div class="row">
          <div class="col-lg-4 col-sm-12 col-xs-12">
              <div class="white-box analytics-info">
                  <h3 class="box-title">Total Partner</h3>
                  <ul class="list-inline two-part">
                      <li>
                          <div id="sparklinedash"></div>
                      </li>
                      <li class="text-right">
                        <i class="ti-arrow-up text-success"></i>
                        <span class="counter text-success">{{ partnerCount }}</span>
                      </li>
                  </ul>
              </div>
          </div>
          <div class="col-lg-4 col-sm-12 col-xs-12">
              <div class="white-box analytics-info">
                  <h3 class="box-title">Total Wallet</h3>
                  <ul class="list-inline two-part">
                      <li>
                          <div id="sparklinedash2"></div>
                      </li>
                      <li class="text-right">
                        <i class="ti-arrow-up text-purple"></i>
                        <span class="counter text-purple">{{ wallets }}.00</span>
                      </li>
                  </ul>
              </div>
          </div>
          <div class="col-lg-4 col-sm-12 col-xs-12">
              <div class="white-box analytics-info">
                  <h3 class="box-title">Total Transfer</h3>
                  <ul class="list-inline two-part">
                      <li>
                          <div id="sparklinedash3"></div>
                      </li>
                      <li class="text-right"><i class="ti-arrow-up text-info"></i>
                        <span class="counter text-info">{{ transfersCount }}.00</span>
                      </li>
                  </ul>
              </div>
          </div>
          <div class="col-lg-3 col-sm-6 col-xs-12" v-show="false">
              <div class="white-box analytics-info">
                  <h3 class="box-title">Total Cancel</h3>
                  <ul class="list-inline two-part">
                      <li>
                          <div id="sparklinedash4"></div>
                      </li>
                      <li class="text-right"><i class="ti-arrow-down text-danger"></i> <span class="text-danger">12,321.00</span></li>
                  </ul>
              </div>
          </div>
      </div>
      <div class="row">
          <div class="col-md-12 col-lg-8 col-sm-12 col-xs-12" v-show="false">
              <div class="white-box">
                  <h3 class="box-title">Transaction Yearly Transfer</h3>
                  <ul class="list-inline text-right">
                      <li>
                          <h5><i class="fa fa-circle m-r-5 text-info"></i>Approved</h5>
                      </li>
                      <li>
                          <h5><i class="fa fa-circle m-r-5 text-inverse"></i>Cancel</h5>
                      </li>
                  </ul>
                  <div id="ct-visits" style="height: 405px;"></div>
              </div>
          </div>
          <div class="col-lg-6 col-md-6 col-sm-6">
              <div class="panel">
                  <div class="sk-chat-widgets">
                      <div class="panel panel-default">
                          <div class="panel-heading">
                              Partner Listing
                          </div>
                          <div class="panel-body">
                              <ul class="chatonline">
                                  <li v-for="partner in partners">
                                      <a>
                                        <img src="~/assets/images/users/varun.jpg" class="img-circle">
                                          <span>
                                            {{ partner.partnerName }}
                                            <small class="text-success">{{ partner.country }}</small>
                                        </span>
                                      </a>
                                  </li>
                              </ul>
                          </div>
                      </div>
                  </div>
              </div>
          </div>
          <div class="col-md-6 col-lg-6 col-sm-6">
              <div class="white-box">
                  <div class="col-md-3 col-sm-4 col-xs-6 pull-right" v-show="false">
                      <select class="form-control pull-right row b-none">
                          <option>March 2020</option>
                          <option>April 2020</option>
                          <option>May 2020</option>
                          <option>June 2020</option>
                          <option>July 2020</option>
                      </select>
                  </div>
                  <h3 class="box-title">Recent Transfer</h3>
                  <div class="row sales-report" v-show="false">
                      <div class="col-md-6 col-sm-6 col-xs-6">
                          <h2>March 2020</h2>
                          <p>Transfer Report</p>
                      </div>
                      <div class="col-md-6 col-sm-6 col-xs-6 ">
                          <h1 class="text-right text-info m-t-20">120,690.00</h1>
                      </div>
                  </div>
                  <div class="table-responsive">
                      <table class="table">
                          <thead>
                              <tr>
                                  <th>#</th>
                                  <th>Partner</th>
                                  <th>STATUS</th>
                                  <th>DATE</th>
                                  <th>Amount</th>
                              </tr>
                          </thead>
                          <tbody>
                              <tr v-for="transfer,index in transfers">
                                  <td>{{ index + 1 }}</td>
                                  <td class="txt-oflo">{{ getPartnerName(transfer.from_partner) }}</td>
                                  <td><span class="label label-success label-rouded">Approved</span> </td>
                                  <td class="txt-oflo">{{ transfer.updatedAt }}</td>
                                  <td><span class="text-success">{{ transfer.fee }}.00</span></td>
                              </tr>
                          </tbody>
                      </table>
                  </div>
              </div>
          </div>
          <div class="col-md-12 col-lg-6 col-sm-12" v-show="false">
              <div class="panel">
                  <div class="panel-heading">MANAGE USERS</div>
                  <div class="table-responsive">
                      <table class="table table-hover manage-u-table">
                          <thead>
                              <tr>
                                  <th style="width: 70px;" class="text-center">#</th>
                                  <th>NAME</th>
                                  <th>ROLE</th>
                                  <th>EMAIL</th>
                                  <th>MANAGE</th>
                              </tr>
                          </thead>
                          <tbody>
                              <tr>
                                  <td class="text-center">1</td>
                                  <td>
                                      <span class="font-medium">Daniel Kristeen</span>
                                      <br /><span class="text-muted">Bangkok, Thailand</span>
                                  </td>
                                  <td>
                                      Administrator
                                      <br /><span class="text-muted">Past : Support</span>
                                  </td>
                                  <td>
                                      daniel@website.com
                                      <br /><span class="text-muted">999 - 444 - 555</span>
                                  </td>
                                  <td>
                                      <button type="button" class="btn btn-info btn-outline btn-circle btn-lg m-r-5"><i class="icon-trash"></i></button>
                                      <button type="button" class="btn btn-info btn-outline btn-circle btn-lg m-r-5"><i class="ti-pencil-alt"></i></button>
                                  </td>
                              </tr>
                              <tr>
                                  <td class="text-center">1</td>
                                  <td>
                                      <span class="font-medium">Daniel Kristeen</span>
                                      <br /><span class="text-muted">Bangkok, Thailand</span>
                                  </td>
                                  <td>
                                      Administrator
                                      <br /><span class="text-muted">Past : Support</span>
                                  </td>
                                  <td>
                                      daniel@website.com
                                      <br /><span class="text-muted">999 - 444 - 555</span>
                                  </td>
                                  <td>
                                      <button type="button" class="btn btn-info btn-outline btn-circle btn-lg m-r-5"><i class="icon-trash"></i></button>
                                      <button type="button" class="btn btn-info btn-outline btn-circle btn-lg m-r-5"><i class="ti-pencil-alt"></i></button>
                                  </td>
                              </tr>
                              <tr>
                                  <td class="text-center">1</td>
                                  <td>
                                      <span class="font-medium">Daniel Kristeen</span>
                                      <br /><span class="text-muted">Bangkok, Thailand</span>
                                  </td>
                                  <td>
                                      Administrator
                                      <br /><span class="text-muted">Past : Support</span>
                                  </td>
                                  <td>
                                      daniel@website.com
                                      <br /><span class="text-muted">999 - 444 - 555</span>
                                  </td>
                                  <td>
                                      <button type="button" class="btn btn-info btn-outline btn-circle btn-lg m-r-5"><i class="icon-trash"></i></button>
                                      <button type="button" class="btn btn-info btn-outline btn-circle btn-lg m-r-5"><i class="ti-pencil-alt"></i></button>
                                  </td>
                              </tr>
                              <tr>
                                  <td class="text-center">1</td>
                                  <td>
                                      <span class="font-medium">Daniel Kristeen</span>
                                      <br /><span class="text-muted">Bangkok, Thailand</span>
                                  </td>
                                  <td>
                                      Administrator
                                      <br /><span class="text-muted">Past : Support</span>
                                  </td>
                                  <td>
                                      daniel@website.com
                                      <br /><span class="text-muted">999 - 444 - 555</span>
                                  </td>
                                  <td>
                                      <button type="button" class="btn btn-info btn-outline btn-circle btn-lg m-r-5"><i class="icon-trash"></i></button>
                                      <button type="button" class="btn btn-info btn-outline btn-circle btn-lg m-r-5"><i class="ti-pencil-alt"></i></button>
                                  </td>
                              </tr>
                              <tr>
                                  <td class="text-center">1</td>
                                  <td>
                                      <span class="font-medium">Daniel Kristeen</span>
                                      <br /><span class="text-muted">Bangkok, Thailand</span>
                                  </td>
                                  <td>
                                      Administrator
                                      <br /><span class="text-muted">Past : Support</span>
                                  </td>
                                  <td>
                                      daniel@website.com
                                      <br /><span class="text-muted">999 - 444 - 555</span>
                                  </td>
                                  <td>
                                      <button type="button" class="btn btn-info btn-outline btn-circle btn-lg m-r-5"><i class="icon-trash"></i></button>
                                      <button type="button" class="btn btn-info btn-outline btn-circle btn-lg m-r-5"><i class="ti-pencil-alt"></i></button>
                                  </td>
                              </tr>
                              <tr>
                                  <td class="text-center">1</td>
                                  <td>
                                      <span class="font-medium">Daniel Kristeen</span>
                                      <br /><span class="text-muted">Bangkok, Thailand</span>
                                  </td>
                                  <td>
                                      Administrator
                                      <br /><span class="text-muted">Past : Support</span>
                                  </td>
                                  <td>
                                      daniel@website.com
                                      <br /><span class="text-muted">999 - 444 - 555</span>
                                  </td>
                                  <td>
                                      <button type="button" class="btn btn-info btn-outline btn-circle btn-lg m-r-5"><i class="icon-trash"></i></button>
                                      <button type="button" class="btn btn-info btn-outline btn-circle btn-lg m-r-5"><i class="ti-pencil-alt"></i></button>
                                  </td>
                              </tr>
                          </tbody>
                      </table>
                  </div>
              </div>
          </div>
      </div>
  </div>
</template>
<script>
  export default {
    data () {
      return {
      }
    },
    computed: {
      partners () {
        return this.$nuxt.$store.state.partners
      },
      wallets () {
        return this.$nuxt.$store.state.partners.walletUser
      },
      partnerCount () {
        return this.$nuxt.$store.state.partners.length
      },
      transfersCount () {
        let transfers = this.$nuxt.$store.state.transfers
        let fee = 0;
        for (var i = 0; i < transfers.length; i++) {
          fee = fee + transfers[i].fee
        }
        return fee
      },
      transfers () {
        return this.$nuxt.$store.state.transfers
      },
      wallets () {
        let wallets = this.$nuxt.$store.state.wallets
        let fee = 0;
        if (wallets) {
          for (var i = 0; i < wallets.length; i++) {
            fee = fee + wallet[i].amount
          }
        }
        return fee
      }
    },
    methods: {
      getPartnerName (id) {
        let partners = this.$nuxt.$store.state.partners
        let partner = "";
        for (var i = 0; i < partners.length; i++) {
          if (partners[i].id == id) {
            partner = partners[i].partnerName
          }
        }
        return partner
      }
    },
    components: {
    }
  }
</script>
