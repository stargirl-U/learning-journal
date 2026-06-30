# Learning Journal - Reverse Engineering 🚀

Repositori ini berisi catatan belajar mingguan saya selama proses pembelajaran Reverse Engineering. Jurnal ini mendokumentasikan pemahaman konsep, kendala, serta perkembangan adaptasi tools RE dari minggu ke minggu.

---

# Entri #1 — Pengenalan Reverse Engineering

**Tanggal:** 2026-03-09 | **Minggu ke-:** 1

Minggu ini saya mempelajari konsep dasar Reverse Engineering dan alasan mengapa bidang ini penting dalam dunia keamanan siber. Saya mulai dengan membaca materi perkuliahan dan mencari referensi tambahan mengenai proses menganalisis sebuah program tanpa memiliki source code. Dari proses tersebut saya memahami bahwa Reverse Engineering tidak hanya digunakan untuk membobol suatu aplikasi, tetapi juga untuk analisis keamanan, memahami cara kerja software, serta menemukan kerentanan.

Namun, saya masih merasa bingung membedakan secara jelas kapan suatu analisis disebut analisis statis dan kapan termasuk analisis dinamis. Saya menduga hal ini karena saya masih belum memiliki banyak pengalaman praktik menggunakan tools Reverse Engineering. Untuk mengatasinya, saya berencana mencoba langsung beberapa contoh program sederhana agar dapat melihat perbedaan kedua metode tersebut secara nyata.

Secara keseluruhan, minggu pertama ini memberikan gambaran dasar mengenai apa yang akan dipelajari selama satu semester. Saya menjadi lebih termotivasi karena ternyata Reverse Engineering jauh lebih luas daripada yang saya bayangkan.

---

# Entri #2 — Instalasi Tools Reverse Engineering

**Tanggal:** 2026-03-16 | **Minggu ke-:** 2

Minggu ini saya mempelajari penggunaan beberapa tools yang umum digunakan dalam Reverse Engineering seperti Ghidra, x64dbg, Detect It Easy (DIE), dan PE-bear. Saya menginstal seluruh aplikasi tersebut di komputer dan mencoba membuka beberapa file executable sederhana untuk melihat informasi yang dapat ditampilkan oleh masing-masing tools. Dari kegiatan tersebut saya memahami bahwa setiap tools memiliki fungsi yang berbeda, misalnya Ghidra untuk proses disassembly dan decompile, sedangkan DIE digunakan untuk mengenali compiler maupun packer yang digunakan oleh suatu binary.

Bagian yang masih membuat saya bingung adalah tampilan Ghidra yang memiliki banyak jendela dan fitur. Saya menduga kebingungan tersebut muncul karena saya baru pertama kali menggunakan software dengan antarmuka yang cukup kompleks. Saya berencana mengikuti tutorial penggunaan Ghidra sambil mencoba beberapa binary sederhana agar lebih terbiasa.

Secara keseluruhan, saya mulai merasa lebih percaya diri karena seluruh tools yang diperlukan sudah berhasil dipasang dan dapat digunakan dengan baik.

---

# Entri #3 — Mengenal Struktur File PE

**Tanggal:** 2026-03-23 | **Minggu ke-:** 3

Minggu ini saya mempelajari struktur file Portable Executable (PE) yang digunakan pada sistem operasi Windows. Saya mencoba membuka sebuah file executable menggunakan PE-bear dan memperhatikan bagian header, section, serta informasi compiler yang tersedia. Dari praktik tersebut saya mulai memahami bahwa sebuah file executable memiliki struktur tertentu yang dapat memberikan banyak informasi sebelum program dijalankan.

Hal yang masih membingungkan saya adalah fungsi setiap section seperti .text, .data, dan .rdata beserta hubungannya ketika program sedang berjalan. Saya menduga saya masih kurang memahami proses kompilasi sehingga sulit membayangkan bagaimana section tersebut digunakan oleh sistem operasi. Saya berencana membaca dokumentasi format PE dan mencoba membandingkan beberapa executable yang berbeda.

Secara keseluruhan, saya merasa mulai memahami bahwa analisis statis tidak selalu membutuhkan proses menjalankan program karena banyak informasi yang sudah dapat diperoleh dari struktur file.

---

# Entri #4 — Analisis Strings

**Tanggal:** 2026-03-30 | **Minggu ke-:** 4

Minggu ini saya mempelajari bagaimana mencari informasi penting melalui analisis strings pada sebuah binary. Saya mencoba menggunakan fitur Strings di Ghidra dan FLOSS untuk melihat teks yang tersimpan di dalam executable. Dari hasil percobaan tersebut saya memahami bahwa string seperti pesan kesalahan, nama fungsi, maupun petunjuk password sering kali dapat membantu memahami alur program.

Saya masih merasa bingung ketika menemukan string yang telah diobfuscasi atau tidak dapat dibaca secara langsung. Saya menduga hal tersebut terjadi karena beberapa program menggunakan teknik proteksi agar lebih sulit dianalisis. Saya berencana mempelajari teknik deobfuscation dan mencoba lebih banyak contoh binary yang memiliki tingkat kesulitan berbeda.

Secara keseluruhan, saya mulai menyadari bahwa analisis strings merupakan langkah awal yang cukup efektif sebelum melakukan analisis yang lebih mendalam.

---

# Entri #5 — Mengerjakan CrackMe Pertama

**Tanggal:** 2026-04-06 | **Minggu ke-:** 5

Minggu ini saya mencoba menyelesaikan challenge CrackMe pertama dari crackmes.one. Saya membuka file menggunakan Detect It Easy terlebih dahulu, kemudian melanjutkan analisis menggunakan Ghidra untuk mencari fungsi yang berhubungan dengan proses validasi input. Dari proses tersebut saya mulai memahami bagaimana program melakukan pemeriksaan password menggunakan fungsi pembanding string.

Bagian yang masih membingungkan saya adalah cara mengikuti alur program ketika terdapat banyak fungsi yang saling memanggil. Saya menduga saya masih belum terbiasa membaca kode hasil decompile sehingga sering kehilangan konteks. Saya berencana berlatih menggunakan fitur Function Graph di Ghidra agar lebih mudah mengikuti alur eksekusi program.

Secara keseluruhan, saya merasa cukup senang karena akhirnya dapat menyelesaikan challenge pertama meskipun membutuhkan waktu yang cukup lama.

---

# Entri #6 — Dasar Debugging Menggunakan x64dbg

**Tanggal:** 2026-04-13 | **Minggu ke-:** 6

Minggu ini saya mulai mempelajari dasar debugging menggunakan x64dbg. Saya mencoba menjalankan sebuah executable, memasang breakpoint pada fungsi tertentu, lalu mengamati perubahan nilai register ketika program dieksekusi. Dari latihan tersebut saya memahami bahwa debugging memungkinkan saya melihat perilaku program secara langsung saat berjalan.

Saya masih sering bingung menentukan lokasi breakpoint yang tepat karena belum sepenuhnya memahami alur eksekusi program. Saya menduga hal ini terjadi karena saya masih menghafal fungsi-fungsi dasar debugger tanpa memahami tujuan penggunaannya. Saya berencana mencoba lebih banyak latihan debugging pada program sederhana agar lebih terbiasa.

Secara keseluruhan, saya merasa kemampuan saya mulai berkembang karena kini tidak hanya memahami analisis statis tetapi juga mulai mengenal analisis dinamis.

---

# Entri #7 — Import Table dan API Windows

**Tanggal:** 2026-04-20 | **Minggu ke-:** 7

Minggu ini saya mempelajari import table dan bagaimana sebuah program menggunakan API Windows. Saya mencoba melihat daftar library yang diimpor menggunakan PE-bear dan menghubungkannya dengan fungsi-fungsi yang muncul di Ghidra. Dari kegiatan tersebut saya memahami bahwa daftar import dapat memberikan petunjuk mengenai kemampuan atau tujuan suatu program.

Saya masih mengalami kesulitan mengingat fungsi dari setiap Windows API yang muncul dalam daftar import. Saya menduga penyebabnya adalah jumlah API yang sangat banyak sehingga tidak mudah dihafalkan. Saya berencana lebih sering membaca dokumentasi resmi Microsoft ketika menemukan API yang belum saya kenal.

Secara keseluruhan, saya merasa analisis import table sangat membantu untuk memperkirakan perilaku sebuah binary sebelum melakukan analisis yang lebih mendalam.

---

# Entri #8 — Refleksi Pembelajaran Reverse Engineering

**Tanggal:** 2026-04-27 | **Minggu ke-:** 8

Minggu ini saya lebih banyak melakukan review terhadap seluruh materi yang telah dipelajari selama beberapa minggu terakhir. Saya mencoba mengulang kembali proses analisis mulai dari melihat struktur file, mencari strings, memeriksa import table, hingga membaca hasil decompile menggunakan Ghidra. Dari proses tersebut saya menyadari bahwa langkah-langkah analisis menjadi lebih mudah dipahami dibandingkan ketika pertama kali belajar.

Saya masih merasa perlu meningkatkan kemampuan membaca kode assembly karena masih membutuhkan waktu cukup lama untuk memahami setiap instruksi. Saya menduga hal ini hanya dapat diatasi melalui latihan yang konsisten dan mengerjakan lebih banyak challenge Reverse Engineering. Saya berencana melanjutkan latihan menggunakan CrackMe dengan tingkat kesulitan yang lebih tinggi secara bertahap.

Secara keseluruhan, saya merasa telah mengalami perkembangan yang cukup baik selama delapan minggu pembelajaran. Walaupun masih banyak hal yang harus dipelajari, saya menjadi lebih percaya diri untuk melakukan analisis binary sederhana menggunakan tools yang telah dipelajari.
