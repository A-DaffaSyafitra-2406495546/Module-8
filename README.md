1. Unary mengirim satu request dan menerima satu response, cocok untuk proses sederhana seperti payment. Server streaming menerima satu request lalu mengirim banyak response, cocok untuk data besar seperti riwayat transaksi. Bi-directional streaming membuat client dan server bisa saling mengirim banyak pesan, cocok untuk chat real-time.

2. Security yang perlu diperhatikan adalah authentication untuk memastikan identitas client, authorization untuk membatasi akses method tertentu, dan encryption seperti TLS agar data tidak mudah dibaca pihak lain.

3. Tantangan bidirectional streaming adalah menangani banyak pesan async, koneksi yang bisa putus, backpressure, error stream, dan sinkronisasi state chat agar tidak kacau.

4. ReceiverStream mudah dipakai karena langsung mengubah mpsc receiver menjadi stream yang cocok untuk tonic. Kekurangannya, perlu mengatur buffer dan backpressure dengan benar agar tidak boros memori atau kehilangan performa.

5. Kode bisa dibuat lebih modular dengan memisahkan proto, implementasi service, dan client logic ke module berbeda. Struktur ini membuat kode lebih mudah dites dan dikembangkan.

6. Untuk payment yang lebih kompleks, service perlu validasi input, pengecekan saldo, integrasi payment gateway, database transaction, logging, retry, dan error handling yang jelas.

7. gRPC membuat arsitektur distributed system lebih contract-based melalui proto. Ini membantu interoperabilitas antar bahasa, tetapi membutuhkan tooling dan schema management yang rapi.

8. HTTP/2 mendukung multiplexing, header compression, dan streaming sehingga efisien untuk gRPC. Dibanding HTTP/1.1 atau WebSocket, konfigurasi dan debugging bisa lebih kompleks.

9. REST biasanya memakai request-response satu arah sehingga kurang natural untuk real-time. gRPC bidirectional streaming lebih responsif karena client dan server bisa terus bertukar pesan dalam satu koneksi.

10. Protobuf membuat payload lebih konsisten, cepat, dan type-safe karena berbasis schema. JSON lebih fleksibel dan mudah dibaca manusia, tetapi lebih rentan tidak konsisten jika kontraknya tidak dijaga.
