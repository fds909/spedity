<template>
    <header>
        <nav class="navbar navbar-expand-lg navbar-light border-bottom">
            <div class="container-fluid d-flex ">

                <!-- Navbar-left -->
                <div class="navbar-left d-flex">

                    <a class="navbar-brand" href="#">
                        <img class="brand-logo" src="../assets/img/logo.svg" alt="Spedity Logo">
                    </a>

                    <div class="collapse navbar-collapse" id="navbarNavDropdown">
                        <ul class="navbar-nav">

                            <li class="nav-item">
                                <a class="nav-link" href="#">Le mie richieste</a>
                            </li>

                            <li class="nav-item">
                                <a class="nav-link" href="#">Le mie spedizioni</a>
                            </li>

                            <li class="nav-item">
                                <a class="nav-link" href="#">Archivio</a>
                            </li>

                        </ul>
                    </div>

                </div>

                <!-- Navbar right -->
                <div class="navbar-right d-flex">

                    <div>
                        <ul class="navbar-nav">

                            <li class="nav-item d-flex align-items-center mx-3">
                                <span>Benvenuto {{userMail}} </span>
                                <img class="user-icon" src="@/assets/icons/user-icon.svg" alt="User Logo">
                                <span class="arrow-down">&#9662;</span>
                            </li>

                            <li class="nav-item mx-3">
                                <a class="btn btn-primary" href="#">Invia nuova richiesta</a>
                            </li>

                        </ul>
                    </div>

                </div>

            </div>
        </nav>
    </header>
</template>

<script>
export default {
  name: 'HeaderComp',
  data() {
    return {

    }
  },
  props: ['userMail'],
}
</script>

<style lang="scss">
@import '@/assets/styles/palette.scss';

    .brand-logo {
        height: 50px;
    }

    .navbar-left {
        font-weight: bold;
    }

    .user-icon {
        height: 20px;
        width: 20px;
        margin-left: 8px;
        margin-right: 5px;
    }

    .arrow-down {
        font-size: 22px;
    }
    
</style>