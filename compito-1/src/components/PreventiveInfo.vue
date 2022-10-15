<template>
    <div id="preventive-info" class="border rounded my-2">
        <div class="container-fluid">
            <div class="row">

                <div class="col">
                    <!-- Shipping Date -->
                    <div class="info-text">
                        <span class="circle border">
                            <img src="@/assets/icons/chevron-up.svg" alt="Up"/>
                        </span>
                        <span>{{prevInfo.shippingDate}}</span>
                    </div>

                    <!-- Priority -->
                    <div class="info-text">
                        <span class="circle border">
                            <img src="@/assets/icons/chevron-down.svg" alt="Down"/>
                        </span>
                        <span>{{prevInfo.priority}}</span>
                    </div>
                </div>


                <div class="col">
                    <!-- Departure Place -->
                    <div class="info-text">
                        <span class="circle border">
                            <img src="@/assets/icons/chevron-up.svg" alt="Up"/>
                        </span>
                        <span>{{prevInfo.departurePlace.cap}} - {{prevInfo.departurePlace.city}} 
                                ({{prevInfo.departurePlace.province}})</span>
                    </div>
                    
                    <!-- Delivery Place -->
                    <div class="info-text">
                        <span class="circle border">
                            <img src="@/assets/icons/chevron-up.svg" alt="Up"/>
                        </span>
                        <span>{{prevInfo.deliveryPlace.cap}} - {{prevInfo.deliveryPlace.city}} 
                                ({{prevInfo.deliveryPlace.province}})</span>
                    </div>
                </div>


                <div class="col">
                    <!-- Pallet -->
                    <div class="info-text">
                        <span><strong>Pallet : </strong> {{prevInfo.pallet.weight}}Kg {{prevInfo.pallet.length}}x
                                {{prevInfo.pallet.height}}x{{prevInfo.pallet.width}}cm Qta:{{prevInfo.pallet.quantity}}
                        </span>
                    </div>
                </div>
                
                <div class="col">
                    <!-- Offers -->
                    <div class="info-text">
                        Nessuna offerta ricevuta
                    </div>
                </div>

                <div class="col-3">
                    <div class="info-text">
                        <span class="label-green rounded rounded-pill fw-bold">Scade il {{prevInfo.expirDate}} alle {{prevInfo.expirTime}}</span>
                    </div>
                </div>

                <div class="col">
                    <!-- Detail button -->
                    <a :class="(showDetail)?'btn btn-secondary btn-active':'btn btn-secondary'"
                        href="#" @click="toggleDetail">Dettaglio &#9660;</a>
                </div>
            </div>
        </div>

        <DetailComp v-show="showDetail" :detail="prevInfo"/>
    </div>
</template>

<script>
import DetailComp from './DetailComp.vue';

export default {
  name: 'PreventiveInfo',
  components: {
    DetailComp
  },
  data() {
    return {
        prevInfo: {
            shippingId: 'ffc78c0b',
            priority: 'Standard',
            message: '',
            content: 'Merce generica',
            value: 300,
            pallet: {
                weight: 100,
                height: 100,
                length: 100,
                width: 100,
                quantity: 1
            },
            shippingDate: '14/10/2022',
            departurePlace: {
                city: 'Sora',
                cap: '03039',
                province: 'FR'
            },
            deliveryPlace: {
                city: 'Vivaro Romano',
                cap: '00020',
                province: 'RM'
            },
            expirDate: '24/10/2022',
            expirTime: '0:00',
            vehicleEquip: 'Sponda Idraulica  Alza/Abbassa',
            extraServ: ''
        },

        showDetail: false,
    }
  },
  props: [],
  methods: {
    toggleDetail() {
        this.showDetail = !this.showDetail;
    }
  }
}
</script>

<style lang="scss" scoped>
@import '@/assets/styles/palette.scss';

    #preventive-info {
        background-color: $lightgrey;
        padding: 20px;
        font-size: 12px;
    }

    .circle {
        background-color: white;
        width: 20px;
        height: 20px;
        border-radius: 50%;
        display: flex;
        justify-content: center;
        align-items: center;
        margin-right: 5px;
    }

    .circle img {
        height: 10px;
        width: 10px;
    }

    .info-text {
        display: flex;
        margin-bottom: 5px;
    }
</style>