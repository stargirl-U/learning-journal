# Learning Journal - Reverse Engineering 🚀

Repositori ini berisi catatan belajar mingguan saya selama proses pembelajaran Reverse Engineering. Jurnal ini mendokumentasikan pemahaman konsep, kendala, serta perkembangan adaptasi tools RE dari minggu ke minggu.

---

### Jurnal #1 (Minggu 1)
* **Tanggal:** 13 Mei 2026
* **Topik:** Pengenalan Arsitektur x86/x64 dan Pembuatan Environment Kerja GitHub

Minggu ini saya mempelajari konsep dasar Reverse Engineering dan alasan mengapa bidang ini penting dalam dunia keamanan siber. Saya mulai dengan membaca materi perkuliahan dan mencari referensi tambahan mengenai proses menganalisis sebuah program tanpa memiliki source code. Dari proses tersebut saya memahami bahwa Reverse Engineering tidak hanya digunakan untuk membobol suatu aplikasi, tetapi juga untuk analisis keamanan, memahami cara kerja software, serta menemukan kerentanan.

Namun, saya masih merasa bingung membedakan secara jelas kapan suatu analisis disebut analisis statis dan kapan termasuk analisis dinamis. Saya menduga hal ini karena saya masih belum memiliki banyak pengalaman praktik menggunakan tools Reverse Engineering. Untuk mengatasinya, saya berencana mencoba langsung beberapa contoh program sederhana agar dapat melihat perbedaan kedua metode tersebut secara nyata.

Secara keseluruhan, minggu pertama ini memberikan gambaran dasar mengenai apa yang akan dipelajari selama satu semester. Saya menjadi lebih termotivasi karena ternyata Reverse Engineering jauh lebih luas daripada yang saya bayangkan.


---

### Jurnal #2 (Minggu 2)
* **Tanggal:** 20 Mei 2026
* **Topik:** Instalasi Tools Analisis (Ghidra & x64dbg) di Lingkungan Terisolasi

Minggu ini saya mempelajari penggunaan beberapa tools yang umum digunakan dalam Reverse Engineering seperti Ghidra, x64dbg, Detect It Easy (DIE), dan PE-bear. Saya menginstal seluruh aplikasi tersebut di komputer dan mencoba membuka beberapa file executable sederhana untuk melihat informasi yang dapat ditampilkan oleh masing-masing tools. Dari kegiatan tersebut saya memahami bahwa setiap tools memiliki fungsi yang berbeda, misalnya Ghidra untuk proses disassembly dan decompile, sedangkan DIE digunakan untuk mengenali compiler maupun packer yang digunakan oleh suatu binary.

Bagian yang masih membuat saya bingung adalah tampilan Ghidra yang memiliki banyak jendela dan fitur. Saya menduga kebingungan tersebut muncul karena saya baru pertama kali menggunakan software dengan antarmuka yang cukup kompleks. Saya berencana mengikuti tutorial penggunaan Ghidra sambil mencoba beberapa binary sederhana agar lebih terbiasa.

Secara keseluruhan, saya mulai merasa lebih percaya diri karena seluruh tools yang diperlukan sudah berhasil dipasang dan dapat digunakan dengan baik.


---

### Jurnal #3 (Minggu 3)
* **Tanggal:** 27 Mei 2026
* **Topik:** Dasar-Dasar Bahasa Assembly dan Register CPU

Minggu ini saya mempelajari struktur file Portable Executable (PE) yang digunakan pada sistem operasi Windows. Saya mencoba membuka sebuah file executable menggunakan PE-bear dan memperhatikan bagian header, section, serta informasi compiler yang tersedia. Dari praktik tersebut saya mulai memahami bahwa sebuah file executable memiliki struktur tertentu yang dapat memberikan banyak informasi sebelum program dijalankan.

Hal yang masih membingungkan saya adalah fungsi setiap section seperti .text, .data, dan .rdata beserta hubungannya ketika program sedang berjalan. Saya menduga saya masih kurang memahami proses kompilasi sehingga sulit membayangkan bagaimana section tersebut digunakan oleh sistem operasi. Saya berencana membaca dokumentasi format PE dan mencoba membandingkan beberapa executable yang berbeda.

Secara keseluruhan, saya merasa mulai memahami bahwa analisis statis tidak selalu membutuhkan proses menjalankan program karena banyak informasi yang sudah dapat diperoleh dari struktur file.


---

### Jurnal #4 (Minggu 4)
* **Tanggal:** 03 Juni 2026
* **Topik:** Memahami Control Flow, Instruksi Jump, dan Loops
* **Apa yang Dipahami:** Saya memahami bahwa logika pemrograman seperti `if-else` dan `loops` di tingkat tinggi akan diterjemahkan menjadi instruksi *conditional jump* di tingkat assembly. Contohnya adalah penggunaan `JE` (Jump if Equal), `JNE` (Jump if Not Equal), dan `JMP` (Unconditional Jump) setelah adanya instruksi `CMP` atau `TEST`. Struktur ini membentuk *Control Flow Graph* (CFG) yang dapat kita visualisasikan dalam bentuk grafik blok di Ghidra untuk mempermudah analisis jalur eksekusi program.
* **Apa yang Masih Bingung:** Saya terkadang masih bingung membedakan jenis *jump* yang menggunakan perbandingan *signed* (seperti `JG`, `JL`) dan *unsigned* (seperti `JA`, `JB`). Hal ini sering membuat saya salah menganalisis kondisi batas (*boundary condition*) dari sebuah perulangan di dalam binary. Selain itu, melacak alur *nested loops* (perulangan bersarang) yang memiliki banyak percabangan rumit di dalam debugger masih terasa sangat memusingkan buat saya.

---

### Jurnal #5 (Minggu 5)
* **Tanggal:** 10 Juni 2026
* **Topik:** Analisis Fungsi dan Stack Frame (Prologue & Epilogue)
* **Apa yang Dipahami:** Saya memahami bahwa setiap kali sebuah fungsi dipanggil menggunakan instruksi `CALL`, CPU akan mengalokasikan ruang di memori yang disebut *Stack Frame*. Proses pembuatan ruang ini diawali dengan *Function Prologue* (`push ebp; mov ebp, esp`) dan diakhiri dengan *Function Epilogue* (`mov esp, ebp; pop ebp; ret`) untuk mengembalikan kondisi register seperti semula. Variabel lokal di dalam fungsi diakses menggunakan *offset* negatif dari register EBP (misal: `[ebp-0x4]`).
* **Apa yang Masih Bingung:** Saya masih bingung dalam mengidentifikasi berbagai macam *Calling Conventions* (seperti `__cdecl`, `__stdcall`, dan `__fastcall`) secara cepat saat melihat kode assembly yang mentah. Perbedaan cara pembersihan stack pasca-fungsi dieksekusi oleh pemanggil (*caller*) atau yang dipanggil (*callee*) sering membuat analisis alur fungsi menjadi rumit. Saya juga masih kesulitan mendeteksi parameter apa saja yang dilewatkan ke dalam fungsi jika parameternya berjumlah banyak.

---

### Jurnal #6 (Minggu 6)
* **Tanggal:** 17 Juni 2026
* **Topik:** Pengenalan Format File Portable Executable (PE)
* **Apa yang Dipahami:** Saya memahami bahwa file eksekusi Windows (.exe) menggunakan format PE yang memiliki struktur header berlapis, mulai dari DOS Header, PE Header, Optional Header, hingga Section Table. Bagian *section* yang krusial antara lain `.text` (tempat kode mesin disimpan), `.data` (untuk variabel global yang diinisialisasi), dan `.rdata` (untuk string konstan dan Import Address Table). Mengetahui struktur ini sangat membantu saat melakukan analisis statis awal untuk memetakan isi file.
* **Apa yang Masih Bingung:** Saya masih bingung memahami konsep pemetaan alamat dari *File Offset* (alamat file di harddisk) menjadi *Relative Virtual Address* / RVA (alamat memori saat dieksekusi). Rumus konversi alamat ini sering kali membingungkan saat saya mencoba mencari posisi fungsi secara manual tanpa bantuan tools otomatis. Selain itu, saya juga belum paham bagaimana sistem operasi membaca Base Address jika terjadi tabrakan alamat (*Address Relocation*).

---

### Jurnal #7 (Minggu 7)
* **Tanggal:** 24 Juni 2026
* **Topik:** Teknik Dasar Patching Binary menggunakan Debugger
* **Apa yang Dipahami:** Saya memahami bahwa kita bisa mengubah perilaku suatu program tanpa memiliki kode sumber aslinya dengan teknik *Patching*. Menggunakan x64dbg, saya belajar cara mengubah instruksi *conditional jump* (seperti `JZ`) menjadi instruksi kebalikannya (`JNZ`) atau mengubahnya menjadi `NOP` (*No Operation*) agar bypass proteksi berhasil dilakukan. Teknik ini sangat ampuh digunakan untuk melewati pemeriksaan serial key atau lisensi palsu secara langsung di memori komputer.
* **Apa yang Masih Bingung:** Saya masih bingung bagaimana cara menyimpan hasil *patching* tersebut secara permanen ke dalam file `.exe` yang baru tanpa merusak struktur internal berkas PE tersebut. Terkadang, file yang sudah saya *patch* justru mengalami *crash* atau tidak bisa dibuka kembali setelah disimpan ke penyimpanan lokal. Saya juga belum mengerti bagaimana cara melakukan *patching* pada fungsi yang memiliki proteksi checksum internal berkas.

---

### Jurnal #8 (Minggu 8)
* **Tanggal:** 01 Juli 2026
* **Topik:** Refleksi Akhir Semester dan Teknik Anti-Debugging Dasar
* **Apa yang Dipahami:** Saya memahami bahwa pembuat program sering kali menambahkan proteksi *Anti-Debugging* untuk menyulitkan analis, seperti memanggil API `IsDebuggerPresent()` yang memeriksa flag di PEB (Process Environment Block). Melalui pembelajaran satu semester ini, saya menyadari bahwa Reverse Engineering membutuhkan ketelitian tinggi, pemahaman arsitektur komputer yang kuat, serta kombinasi taktik analisis statis dan dinamis. Seluruh proses pembuatan portofolio ini melatih saya berpikir logis layaknya seorang *security researcher*.
* **Apa yang Masih Bingung:** Saya masih merasa perlu belajar lebih banyak tentang teknik *anti-debugging* tingkat lanjut yang menggunakan *Hardware Breakpoints* atau manipulasi *Exception Handling* (SEH). Pemahaman saya tentang bagaimana mendeteksi dan melewati *binary packing* (seperti UPX tingkat lanjut atau VMProtect) juga masih harus ditingkatkan di luar jam kuliah. Saya masih bingung bagaimana cara terbaik melakukan *unboxing* manual pada binary yang memiliki proteksi enkripsi berlapis.
