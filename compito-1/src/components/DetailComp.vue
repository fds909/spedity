<template>
    <div id="detail" class="border rounded text-white my-4">
        <!-- Heading -->
        <div class="row mb-4">
            <div class="col">
                <h5>Dettagli della tua richiesta</h5>
            </div>
        </div>

        <div class="row row-cols-lg-3 row-cols-sm-1">
            <!-- Col left -->
            <div class="col mb-4">
                <!-- ID -->
                <div class="detail-text mb-3">
                    <strong>Id spedizione: </strong> {{detail.shippingId}}
                </div>

                <!-- Message -->
                <div class="detail-text mb-5">
                    <strong>Il tuo messaggio per il trasportatore: </strong>
                    <div class="text-grey" v-if="detail.message === ''">Nessun messaggio</div>
                    <div v-else>{{detail.message}}</div>
                </div>

                <!-- Content -->
                <div class="detail-text">
                    <strong>Contenuto: </strong> {{detail.content}}
                </div>

                <!-- Value -->
                <div class="detail-text">
                    <strong>Valore: €</strong> {{detail.value}}
                </div>
            </div>

            <!-- Col Center -->
            <div class="col mb-4">
                <!-- Pallet -->
                <div class="detail-text mb-3">
                    <strong>Pallet: </strong> {{detail.pallet.weight}}Kg {{detail.pallet.length}}x{{detail.pallet.height}}x{{detail.pallet.width}}cm Qta:{{detail.pallet.quantity}}
                </div>

                <!-- Dotazione mezzo -->
                <div class="detail-text">
                    <strong>Dotazione mezzo: </strong> {{detail.vehicleEquip}}
                </div>
            </div>

            <!-- Col right -->
            <div class="col mb-4">
                <div class="detail-text">
                    <strong>Servizi aggiuntivi richiesti</strong>
                    <div class="text-grey" v-if="detail.extraServ === ''">Nessuno</div>
                    <div v-else>{{detail.extraServ}}</div>
                </div>
            </div>
        </div>
    </div>
</template>

<script>
export default {
  name: 'DetailComp',
  data() {
    return {

    }
  },
  props: ['detail'],
}
</script>

<style lang="scss" scoped>
@import '@/assets/styles/palette.scss';

    #detail {
        font-size: 16px;
        padding: 20px;
        background-color: $darkergrey;
    }

    .text-grey {
        color: $darkgrey;
    }

</style>