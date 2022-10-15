<template>
    <div id="detail" class="border rounded">
        <!-- Heading -->
        <div class="row">
            <div class="col">
                <h5>Dettagli della tua richiesta</h5>
            </div>
        </div>

        <div class="row">
            <!-- Col left -->
            <div class="col">
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
            <div class="col">
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
            <div class="col">
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
        background-color: white;
        padding: 10px;
    }

    h5 {
        font-size: 14px;
        font-weight: bold;
    }

    .text-grey {
        color: $darkgrey;
    }

    strong {
        font-size: 13px;
    }

</style>