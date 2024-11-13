<template>
    <div class="container-fluid">
        <div class="row">
            <div class="col-lg-12">
                <h2 class="text-center my-4">PEMBAYARAN KAS</h2>
                    <div class="mb-3">
                    </div>
                    <div class="mb-3">
                        <div class="col-mb-3">
                            <input type="text" class="form-control form-control-lg  rounded-5" placeholder="NAMA">
                        </div>
                    </div>
                    <div class="mb-3">
                        <div class="row">
                            <div class="col-mb-3">
                                <input type="text" class="form-control form-control-lg mb-3 rounded-5" placeholder="MASUKKAN NOMINAL">
                            </div>
                        </div>
                    </div>
                    <Nuxt-Link to="/">
                        <button type="submit" class="btn btn-outline-danger rounded-6" style="color: black; font-family: lnria-serif">BATAL</button>
                    </Nuxt-Link>
                    <Nuxt-Link to="/anggota">
                        <button type="submit" class="btn btn-outline-primary rounded-6" style="color: black; font-family: lnria-serif">KIRIM</button>
                    </Nuxt-Link>
            </div>
        </div>
    </div>
</template>