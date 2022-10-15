<template>
    <div id="preventive-info">
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
                        <span class="label-green rounded rounded-pill">Scade il {{prevInfo.expirDate}} alle {{prevInfo.expirTime}}</span>
                    </div>
                </div>

                <div class="col">
                    <!-- Detail -->
                    <a class="btn btn-secondary" href="#" @click="showDetail">Dettaglio &#9660;</a>
                </div>
            </div>
        </div>

        <DetailComp/>
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
            expirTime: '0:00'
        }
    }
  },
  props: [],
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

    .label-green {
        font-weight: bold;
        color: white;
        background-color: $green;
        padding: 5px 10px;
    }
</style>