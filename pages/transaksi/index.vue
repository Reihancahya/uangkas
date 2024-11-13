<!-- Transaction History Component -->
<template>
    <div class="container-fluid">
        <link rel="stylesheet" href="https://cdn.jsdelivr.net/npm/bootstrap-icons@1.11.3/font/bootstrap-icons.min.css">
        <div class="row">
            <div class="col-lg-12">
                <h2 class="text-center my-4"> SISWA</h2>
                <div class="my-3">
                    <!-- <form @submit.prevent="getTransaksi">
                        <input v-model="keyword" type="search" class="form-control rounded-5" placeholder="Cari">
                    </form>
                    <div class="my-3 text-muted"> Menampilkan {{ visitors.length }} dari {{ jumlah }} </div> -->
                    <table class="table">
                        <thead>
                            <tr>
                                <th>No</th>
                                <th>NAMA</th>
                                <th>WAKTU</th>
                                <th>JUMLAH</th>
                            </tr>
                        </thead>
                        <tbody>
                            <tr v-for="(visitor, i) in visitors" :key="i">
                                <td>{{ i + 1 }}.</td>
                                <td>{{ visitor.anggota.nama }}</td>
                                <td>{{ visitor.tanggal }}</td>
                                <td>{{ visitor.jumlah }}</td>
                            </tr>
                        </tbody>
                    </table>
                </div>
            </div>
        </div>
        <NuxtLink to="/">

            <button type="button" class="btn btn-danger btn-lg">Batal</button>
        </NuxtLink>
    </div>
</template>

<script setup>
const supabase = useSupabaseClient()
const keyword = ref('')
const visitors = ref([])
const jumlah = ref(0)

// Fetch transaction data with related anggota and keperluan data
const getTransaksi = async () => {
    const { data, error } = await supabase
        .from('transaksi')
        .select(`*, anggota (nama)`)
        .order('id', { ascending: false })
    if (data) visitors.value = data
}

// Get total count of transactions
const totalPengunjung = async () => {
    const { count, error } = await supabase
        .from('transaksi')
        .select('*', { count: 'exact' })

    if (error) {
        console.error('Error counting data:', error)
    } else {
        jumlah.value = count || 0
    }
}

// Run fetch functions on component mount
onMounted(() => {
    getTransaksi()
    totalPengunjung()
})
</script>

<style scoped>
/* Add any custom styles here */
</style>
