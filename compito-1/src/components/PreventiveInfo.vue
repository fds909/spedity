<template>
    <div id="preventive-info" class="border rounded py-3 px-5">
        <div class="container-fluid">
            <div class="row mb-3 justify-content-center">
                
                <div class="col-lg-6 col-md-8 col-sm-12 d-flex align-items-center justify-content-between">
                    <div class="d-flex flex-column align-items-center">
                        <div class="circle mb-2">
                            <img src="@/assets/icons/location.svg" alt="Location Partenza">
                        </div>
                        <p class="text-center">{{prevInfo.departurePlace.cap}} - 
                            {{prevInfo.departurePlace.city}} ({{prevInfo.departurePlace.province}})</p>

                    </div>

                    <div class="d-flex flex-column align-items-center">
                        <div class="circle mb-2">
                            <img src="@/assets/icons/flag.svg" alt="Flag Destinazione">
                        </div>
                        <p class="text-center">{{prevInfo.deliveryPlace.cap}} - 
                            {{prevInfo.deliveryPlace.city}} ({{prevInfo.deliveryPlace.province}})</p>
                    </div>
                </div>

            </div>

            <div class="row row-cols-xs-1 row-cols-md-1 row-cols-lg-3 mb-3 justify-content-center">

                <!-- Shipping Date + Priority -->
                <div class="col mb-4">
                    <div class="mb-4">
                        <div><strong>Data di partenza</strong></div>
                        <div>{{prevInfo.shippingDate}}</div>
                    </div>
                    <div class="mb-4">
                        <span class="px-2 py-2 bg-black fw-bold text-white rounded">
                            <img class="white-icon me-2" src="@/assets/icons/truck.svg" alt="">
                            {{prevInfo.priority}}
                        </span>
                    </div>
                    <div>
                        <span class="px-2 py-1 bg-yellow text-white rounded">Scade il {{prevInfo.expirDate}} alle {{prevInfo.expirTime}}</span>
                    </div>
                </div>

                <!-- Pallet -->
                <div class="col">
                    <h5 class="text-center">Pallet</h5>
                    <div class="d-flex flex-column align-items-center">
                        <table class="table text-center">
                            <thead>
                                <tr>
                                    <th scope="col">Peso</th>
                                    <th scope="col">Altezza</th>
                                    <th scope="col">Lunghezza</th>
                                    <th scope="col">Quantità</th>
                                </tr>
                            </thead>
                            <tbody>
                                <tr>
                                    <td>{{prevInfo.pallet.weight}} Kg</td>
                                    <td>{{prevInfo.pallet.height}} cm</td>
                                    <td>{{prevInfo.pallet.width}} cm</td>
                                    <td>{{prevInfo.pallet.quantity}}</td>
                                </tr>
                            </tbody>
                        </table>
                    </div>
                </div>


                <div class="col">
                    <h5 class="text-center mb-2">Offerte ricevute</h5>
                    <p class="text-grey text-center">Ancora nessuna offerta</p>
                </div>

            </div>

            <!-- Detail Button -->
            <div class="row justify-content-end">
                <a @click="showDetail = !showDetail" class="d-inline-block w-25 btn btn-secondary" href="#">Dettaglio</a>
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
        showDetail: false,
    }
  },
  props: ['prevInfo']
}
</script>

<style lang="scss" scoped>
@import '@/assets/styles/palette.scss';

    #preventive-info {
        background-color: $lightgrey;
        font-size: 16px;
    }

    .circle {
        background-color: rgb(49, 49, 49);
        width: 60px;
        height: 60px;
        border-radius: 50%;
        display: flex;
        justify-content: center;
        align-items: center;
    }

    .line {
        height: 4px;
        width: 30vw;
        background-color: rgb(77, 77, 77);
    }

    .circle img {
        width: 40%;
        filter: invert(100);
    }

    .info-text {
        display: flex;
        margin-bottom: 5px;
    }

    .bg-yellow {
        background-color: $yellorange;
    }

    .text-grey {
        color: $darkgrey;
    }

    .white-icon {
        width: 25px;
        filter: invert(100%);
    }
</style>