<!-- Transaction Submission Component -->
<template>
  <div class="container-fluid p-5">
    <div class="row">
      <div class="col-lg-12">
        <h2 class="text-center my-4">FORM PEMBAYARAN KAS</h2>
        <form @submit.prevent="kirimData">
          <div class="mb-3">
            <select
              v-model="form.anggota"
              class="form-control form-control-lg form-select rounded-5"
              required
            >
              <option value="">NAMA</option>
              <option
                v-for="(member, i) in members"
                :key="i"
                :value="member.id"
              >
                {{ member.nama }}
              </option>
            </select>
          </div>
          <div class="mb-3">
            <input
              v-model="form.jumlah"
              type="number"
              class="form-control form-control-lg rounded-5"
              placeholder="Jumlah.."
              required
            />
          </div>

          <button type="submit" class="btn btn-lg rounded-5 px-5 bg-primary text-white">KIRIM</button>
          <NuxtLink to="/">
            <button type="button" class="btn btn-lg rounded-5 px-5 bg-danger text-white">BATAL</button>
          </NuxtLink>
        </form>
        <br />
      </div>
    </div>
  </div>
</template>

<script setup>

const supabase = useSupabaseClient()
const router = useRouter()

const members = ref([])
const form = ref({
  jumlah: 0,
  anggota: ""
})

// Function to submit the transaction
const kirimData = async () => {
  const { error } = await supabase.from("transaksi").insert({
    jumlah: form.value.jumlah,
    anggota: form.value.anggota,
    tanggal: new Date().toISOString().split("T")[0]  
  })

  if (error) {
    console.error("Error inserting data:", error)
  } else {
    router.push("/transaksi")  // Navigate to transaction history after submission
  }
}

// Fetch members from 'anggota' table
const getAnggota = async () => {
  const { data, error } = await supabase.from("anggota").select("*")
  if (error) {
    console.error("Error fetching anggota:", error)
  } else {
    members.value = data || []
  }
}

onMounted(() => {
  getAnggota()

})
</script>

<style scoped>

</style>
