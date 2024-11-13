<template>
    <div class="container-fluid">
        <div class="row my-5">
            <div class="col-lg-6">
                <nuxt-link to="/transaksi">
                    <div class="card bg-pemasukan rounded-5">
                        <div class="card-body">
                            <h2>SISWA</h2>
                        </div>
                    </div>
                </nuxt-link>
            </div>
            <div class="col-lg-6">
                <nuxt-link to="/transaksi/tambah">
                    <div class="card bg-pembayaran rounded-5 ">
                        <div class="card-body">
                            <h2>PEMBAYARAN</h2>
                        </div>
                    </div>
                </nuxt-link>
            </div>
            <div class="col-lg-6">
                <nuxt-link to="/siswa">
                    <div class="card bg-laporan rounded-5 mt-5">
                        <div class="card-body">
                            <h2>LAPORAN</h2>
                        </div>
                    </div>
                </nuxt-link>
            </div>
            <div class="col-lg-6">
                <nuxt-link to="/rekapan">
                    <div class="card bg-rekap rounded-5 mt-5">
                        <div class="card-body">
                            <h2>REKAP PENGELUARAN PERMINGGU</h2>
                        </div>
                    </div>
                </nuxt-link>
            </div>
        </div>
    </div>
</template>

<style scoped>
.card {
    height: 250px;
    box-shadow: 1px 1px 1px #424242;
}

.card.bg-pemasukan {
    background-image: url('../assets/img/Uang-Kas-.jpg');
    background-repeat: no-repeat;
    background-position: center center;
    background-size: cover;
}

.card.bg-pembayaran {
    background-image: url('../assets/img/jenis-transaksi-768x403.jpg');
    background-repeat: no-repeat;
    background-position: center center;
    background-size: cover;
}

.card.bg-laporan {
    background-image: url('../assets/img/laporan.webp');
    background-repeat: no-repeat;
    background-position: center center;
    background-size: cover;
}

.card.bg-rekap {
    background-image: url('../assets/img/rekap.jpg');
    background-repeat: no-repeat;
    background-position: center center;
    background-size: cover;
}
</style>
