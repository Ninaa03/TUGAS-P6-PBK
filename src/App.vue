<script setup>
// Synchronous Function: Menghitung jumlah mahasiswa
function hitungMahasiswa(mahasiswaList) {
    // Operasi langsung tanpa delay
    return mahasiswaList.length;
}

// Asynchronous - Callback
function getDataMahasiswaCallback(npm, callback) {
    setTimeout(() => { // Asynchronous
        if (npm === "233510650") {
            callback(null, { npm: npm, nama: "Seri Mehulina br Sinulingga" });
        } else {
            callback("Mahasiswa tidak ditemukan", null);
        }
    }, 2000);
}

// Asynchronous - Promise
function getDataMahasiswaPromise(npm) {
    return new Promise((resolve, reject) => {
        setTimeout(() => { // Asynchronous
            if (npm === "233510650") {
                resolve({ npm: npm, nama: "Seri Mehulina br Sinulingga" });
            } else {
                reject("Mahasiswa tidak ditemukan");
            }
        }, 2000);
    });
}

// Asynchronous - Async/Await
async function showMahasiswa(npm) {
    // Synchronous: Menghitung jumlah mahasiswa
    const mahasiswaList = [
        { npm: "233510650", nama: "Seri Mehulina br Sinulingga" },
        { npm: "233510770", nama: "Aleeina Reinza" },
        { npm: "233510880", nama: "Kayriena Zaeyka" }
    ];
    const totalMahasiswa = hitungMahasiswa(mahasiswaList);
    console.log("Total Mahasiswa (Synchronous):", totalMahasiswa);

    // Asynchronous: Menggunakan await
    try {
        const mahasiswa = await getDataMahasiswaPromise(npm);
        console.log("Mahasiswa ditemukan (Asynchronous):", mahasiswa);
    } catch (error) {
        console.log("Terjadi kesalahan (Asynchronous):", error);
    }
}

// Synchronous: Pemanggilan Fungsi Synchronous
const mahasiswaList = [
    { npm: "233610650", nama: "Seri Mehulina br Sinulingga" },
    { npm: "233510770", nama: "Aleeina Reinza" },
    { npm: "233510880", nama: "Kayriena Zaeyka" }
];
console.log("Pemanggilan Fungsi Synchronous:", hitungMahasiswa(mahasiswaList));

// Asynchronous: Menggunakan callback
getDataMahasiswaCallback("233510650", (error, data) => {
    if (error) {
        console.log("Callback Error (Asynchronous):", error);
    } else {
        console.log("Callback Data (Asynchronous):", data);
    }
});
</script>

<template>
  <div>
    <button @click="showMahasiswa('233510650')">Tampilkan Mahasiswa</button>
    
  </div>
</template>

<style scoped>
button {
  padding: 10px;
  background-color: #007bff;
  color: white;
  border: none;
  border-radius: 5px;
  cursor: pointer;
}

button:hover {
  background-color: #0056b3;
}
</style>