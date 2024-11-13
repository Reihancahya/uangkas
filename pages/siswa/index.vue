<!-- Transaction Submission Component -->
<template>
    <div class="container-fluid p-5">
      <div class="row">
        <div class="col-lg-12">
          <h2 class="text-center my-4">PENGELUARAN</h2>
          <form @submit.prevent="kirimData">
            
            <div class="mb-3">
              <input
                v-model="form.keterangan"
                type="text"
                class="form-control form-control-lg rounded-5"
                placeholder="keterangan"
                required
              />
            </div>
            <div class="mb-3">
              <input
                v-model="form.nominal"
                type="text"
                class="form-control form-control-lg rounded-5"
                placeholder="nominal"
                required
              />
            </div>
  
            <button
              type="submit"
              class="btn btn-lg rounded-5 px-5 bg-primary text-white"
            >
              KIRIM
            </button>
            <NuxtLink to="/">
  
  <button type="button" class="btn btn-danger btn-lg">Batal</button>
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
    keterangan: "",
    nominal: ""
  })
  
  // Function to submit the transaction
  const kirimData = async () => {
    const { error } = await supabase.from("laporan").insert({
      keterangan: form.value.keterangan,
      nominal: form.value.nominal,
    
    })
  
    if (error) {
      console.error("Error inserting data:", error)
    } else {
      router.push("/rekapan")  // Navigate to transaction history after submission
    }
  }
  
  // Fetch members from 'anggota' table
  const getAnggota = async () => {
    const { data, error } = await supabase.from("laporan").select("*")
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
  
