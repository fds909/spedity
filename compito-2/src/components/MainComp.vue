<template>
    <main>
        <div class="container-narrow">
            <div class="container-fluid">
                <!-- Progress steps -->
                <ProgressStepsComp ref="progress" class="w-50 mx-auto mb-3" :currentActive="progressStep"/>

                <!-- STEP Terms + Payment -->
                <div class="border rounded px-2 py-4" v-if="currentStep === STEPS.TERMS_PAYMETHOD">

                    <!-- Checkbox + Payment Method -->
                    <div id="step-3" class="d-flex flex-column">

                        <div class="heading mb-3 px-2">
                            <h5>Pagamento</h5>
                            <p>Importante! Siete pregati di leggere attentamente ed accettare tutte le seguenti condizioni</p>
                        </div>

                        <div class="mb-3 px-2 d-flex align-items-start">
                            <input v-model="inputState.termCond" type="checkbox">
                            <label for="termCond" class="ms-2">Ho letto ed accetto le clausole riportate nei "Termini e Condizioni"</label>
                        </div>
                        <div class="mb-3 px-2 d-flex align-items-start">
                            <input v-model="inputState.termCondArts" type="checkbox">
                            <label for="termCondArts" class="ms-2">Ho letto ed accetto le clausole riportate nei "Termini e Condizioni di cui agli artt: 3, 5.1, 5.2, 7, 7, 10, 11, 12, 13, 14.1, 14.2, 14.3, 14.4, 15, 17.1, 17.2, 17.3, 17.4, 18, 19, 21.1, 21.2 e 22.</label>
                        </div>
                        <div class="mb-3 px-2 d-flex align-items-start">
                            <input v-model="inputState.rightWeight" type="checkbox">
                            <label for="rightWeight" class="ms-2">Ho capito che se il peso e/o il volume dei colli spediti dovessero essere maggiore rispetto a quello dichiarato al momento dell'acquisto, potrebbe essermi addeitata la differenza di prezzo.</label>
                        </div>
                        <div class="mb-3 px-2 d-flex align-items-start">
                            <input v-model="inputState.rightValue" type="checkbox">
                            <label for="rightValue" class="ms-2">Confermo che il valore dei beni che ho fornito è corretto.</label>
                        </div>
                        <div class="mb-3 px-2 py-3 d-flex align-items-start bg-red rounded">
                            <input v-model="inputState.legal" type="checkbox">
                            <label for="legal" class="ms-2">Confermo di non spedire oggetti con restrizioni e che la mia spedizione non contiene alcool, droghe illegali, ogni altra forma di contrabbando o qualsiasi oggetto che richiede una licenza di trasporto. Accetto che oggetti con restrizioni vengano sequestrati e distrutti senza rimborso alcuno.</label>
                        </div>

                        <hr />

                        <div class="heading mb-3 px-2">
                            <h5>Metodo di pagamento</h5>
                        </div>

                        <div class="row px-2 mb-3">

                            <!-- Left Col Payment Method -->
                            <div class="col px-3">
                                <select v-model="inputState.payMethod" class="form-select" aria-label="Metodo di pagamento">
                                    <option value="" disabled selected>Scegli un metodo di pagamento</option>
                                    <option value="bank-transfer">Bonifico Bancario</option>
                                    <option value="credit-card">Carta di Credito</option>
                                </select>

                                <!-- Stripe Banner -->
                                <img src="@/assets/img/stripe.png" alt="Stripe Banner">
                            </div>

                            <!-- Right Col Order Summary -->
                            <div class="col d-flex flex-column mx-5">
                                <div class="heading">
                                    <h4>Il tuo ordine</h4>
                                </div>
                                <div class="order-info d-flex">
                                    <div class="col">Imponibile</div>
                                    <div class="col">€{{order.taxable.toFixed(2)}}</div>
                                </div>
                                <div class="order-info d-flex">
                                    <div class="col">Iva</div>
                                    <div class="col">€{{order.vat.toFixed(2)}}</div>
                                </div>
                                <div class="order-info d-flex fw-bold">
                                    <div class="col">TOTALE</div>
                                    <div class="col">€{{order.total.toFixed(2)}}</div>
                                </div>
                            </div>
                        </div>

                        <!-- Action Buttons -->
                        <div class="row px-2">
                            <div class="col-3">
                                <button class="btn-back w-100 py-2 rounded rounded-3" disabled>
                                    &larr; Indietro</button>
                            </div>
                            <div class="col">
                                <button @click="confirmPay" class="btn-confirm w-100 py-2 rounded rounded-3">
                                    Conferma ordine e paga ora</button>
                            </div>
                        </div>
                    </div>
                </div>
                <!-- END STEP Terms + Payment -->

                <!-- STEP Confirm Transfer -->
                <div class="border rounded p-4" v-if="currentStep === STEPS.CONFIRM_TRANSFER">
                    <h4 class="text-blue mb-2">Ordine confermato!</h4>

                    <p class="mb-4">Grazie di usare Spedity per le tue spedizioni.</p>

                    <h5 class="mb-2">Cosa succede adesso?</h5>

                    <p>Siamo in attesa del tuo pagamento tramite bonifico bancario.</p>

                    <!-- Tranfer Data -->
                    <div class="my-5">
                        <p class="mb-3">Dovrai effettuare un bonifico con questi dati: </p>
                        <ul class="ps-5">
                            <li class="d-flex mb-2">
                                <div class="col-3"><strong>IBAN</strong></div>
                                <div class="col-6">{{tranfer.iban}}</div>
                            </li>
                            <li class="d-flex mb-2">
                                <div class="col-3"><strong>Beneficiario</strong></div>
                                <div class="col-6">{{tranfer.benefic}}</div>
                            </li>
                            <li class="d-flex mb-2">
                                <div class="col-3"><strong>Importo</strong></div>
                                <div class="col-6">€ {{order.total.toFixed(2)}}</div>
                            </li>
                            <li class="d-flex mb-2">
                                <div class="col-3"><strong>Causale</strong></div>
                                <div class="col-6">{{tranfer.reason}}</div>
                            </li>
                        </ul>
                    </div>

                    <button class="btn-confirm w-100 py-2 rounded rounded-3">
                        Vedi il dettaglio e lo stato del tuo ordine</button>
                </div>
                <!-- END STEP Confirm Transfer -->

                <!-- STEP Credit Card -->
                <div class="border rounded px-4 py-5" v-if="currentStep === STEPS.CREDIT_CARD">
                    <p class="mb-2">Il pagamento con carta di credito è sicuro <br/>
                        Il sistema è gestito da Stripe che si occupa del processo di gestione del pagamento. <br/>
                        Nessun numero di carta viene memorizzato nei nostri sistemi.
                    </p>

                    <hr class="mb-2"/>

                    
                </div>
                <!-- END STEP Credit Card -->

            </div>
        </div>
    </main>
</template>

<script>
import ProgressStepsComp from './ProgressStepsComp.vue'

export default {
    name: 'MainComp',
    components: {
        ProgressStepsComp
    },
    data() {
        return {
            STEPS: {TERMS_PAYMETHOD: 0, CREDIT_CARD: 1, CONFIRM_TRANSFER: 2, CONFIRM_CREDIT: 3},
            currentStep: 1,
            progressStep: 2,
            inputState: {
                termCond: false,
                termCondArts: false,
                rightWeight: false,
                rightValue: false,
                legal: false,
                payMethod: ''
            },
            tranfer: {
                iban: 'IT45R0200874601000104363164',
                benefic: 'Spedity srl',
                reason: 'Pagamento ordine 7C1E9785'
            }
        }
    },
    props: ['order'],
    methods: {
        confirmPay() {

            if (!(this.inputState.termCond && this.inputState.termCondArts && this.inputState.rightWeight
                && this.inputState.rightValue && this.inputState.legal)) {
                alert('Attenzione! Assicurarsi di accettare tutte le voci dei termini e condizioni.');
            } else {
                switch (this.inputState.payMethod) {
                    case '':
                        alert('Attenzione! Selezionare un metodo di pagamento valido.');
                        break;
                    case 'bank-transfer':
                        this.currentStep = this.STEPS.CONFIRM_TRANSFER;
                        this.progressStep++;
                        this.$refs.progress.update();
                        break;
                    case 'credit-card':
                        this.currentStep = this.STEPS.CREDIT_CARD;
                        break;
                }
            }


        }
    }
}
</script>

<style lang="scss" scoped>
@import '@/assets/styles/palette.scss';

    main {
        margin: 30px 0;
    }

    img {
        max-width: 100%;
    }
    .container-narrow {
        width: 50%;
        margin: 0 auto;
    }

    ul {
        list-style-type: none;
    }

    h4 {
        font-weight: bold;
        font-size: 22px;
    }

    h5 {
        font-size: 15px;
        font-weight: bold;
        margin: 0;
    }

    .bg-red {
        background-color: $lightred;
    }

    #step-3 hr {
        padding: 0 20px;
        background-color: $midgrey;
    }

    .btn-back {
        color: black;
        background-color: $darkgrey;

    }

    .btn-confirm {
        color: white;
        background-color: $blue;
    }

    .btn-back,
    .btn-confirm {
        border: 0;
    }

    .text-blue {
        color: $blue,
    }
</style>
