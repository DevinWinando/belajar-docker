# Dockerfile

Berikut adalah instruksi-instruksi yang bisa ditambahkan pada `Dockerfile`.

## FROM INSTRUCTION
Digunakan untuk memanggil image lain.

- Build `Dockerfile`
  ```sh
  docker build -t devinwinando/from "Dockerfile/1. FROM"
  ```

## RUN INSTRUCTION
Digunakan untuk mengeksekusi perintah pada saat build stage.

- Build `Dockerfile`.

  ```sh
  docker build -t devinwinando/run "Dockerfile/2. RUN"
  ```

- Build `Dockerfile` dengan menampilkan outputnya atau menampilkan progres buildnya.
  ```sh
  docker build -t devinwinando/run "Dockerfile/2. RUN" --progress=plain
  ```

- Build `Dockerfile` tanpa cache.
  ```sh
  docker build -t devinwinando/run "Dockerfile/2. RUN" --no-cache
  ```

## COMMAND INSTRUCTION (CMD)
Digunakan untuk mengeksekusi perintah pada saat image dijalankan di dalam container.

- Build `Dockerfile`.

  ```sh
  docker build -t devinwinando/command "Dockerfile/3. COMMAND"
  ```

## LABEL  INSTRUCTION
Digunakan untuk menambahkan metadata.

- Build `Dockerfile`.

  ```sh
  docker build -t devinwinando/label "Dockerfile/4. LABEL"
  ```

## ADD INSTRUCTION
Digunakan untuk menambahkan file dari suatu sumber, bisa dari local ataupun url ke dalam destination di docker image. Untuk menambahkan banyak file sekaligus, gunakan pattern golang.  Berikut link [dokumentasinya](https://pkg.go.dev/path/filepath#Match). Command ini juga akan otomatis mengekstrak file jika filenya berupa file kompresi.

- Build `Dockerfile`.

  ```sh
  docker build -t devinwinando/add "Dockerfile/5. ADD"
  ```

## COPY INSTRUCTION
Mirip seperti instruksi ADD, yaitu digunakan untuk menambahkan file dari suatu sumber, bisa dari local ataupun url Perbedaannya adalah instruksi ini tidak bisa mengambil file dari URL dan tidak akan otomatis mengekstrak file yang bersifat kompresi. Namun instruksi ini adalah best practice dalam pembuatan `Dockerfile`.

- Build `Dockerfile`.

  ```sh
  docker build -t devinwinando/copy "Dockerfile/6. COPY"
  ```

## dockerignore
Digunakan untuk mengabaikan file/folder, mirip seperti `.gitignore`.

- Build `Dockerfile`.

  ```sh
  docker build -t devinwinando/dockerignore "Dockerfile/7. dockerignore"
  ```

## EXPOSE INTRUCTION
Digunakan untuk memberitahu bahwa image akan me-listen pada port atau protocol mana.

- Build `Dockerfile`.

  ```sh
  docker build -t devinwinando/expose "Dockerfile/8. EXPOSE"
  ```

## ENV INTRUCTION
Digunakan untuk menambahkan environtment variable pada image.

## VOLUME INTRUCTION
Digunakan untuk membuat volume secara otomatis ketika image dibuat menjadi container.

- Build `Dockerfile`.
  ```sh
  docker build -t devinwinando/volume "Dockerfile/10. VOLUME"
  ```

## WORKING DIRECTORY INTRUCTION (WORKDIR)
Digunakan untuk menentukan direktori untuk menjalankan instruksi-instruksi lainnya, misalnya ADD, COPY, CMD, dan sebagainya.

- Build `Dockerfile`.
  ```sh
  docker build -t devinwinando/workdir "Dockerfile/11. WORKDIR"
  ```

## USER INTRUCTION
Digunakan untuk mengubah user atau user group yang digunakan ketika docker image dijalankan. Secara default, user yang digunakan adalah `root`, namun ini bisa diubah menggunakan instruksi `USER`.

## ARGUMENT INTRUCTION (ARG)
Digunakan untuk mendefinisikan variabel yang digunakan ketika proses build. Penggunaannya sama seperti `ENV INSTRUCTION`, yang membedakannya adalah `ARG INSTRUCTION` hanya dapat digunakan pada proses build.

## HEALTHCHECk INTRUCTION
Digunakan untuk mengecek container apakah statusnya sehat (healthy) atau tidak sehat (unhealthy). Pengecekan ini bisa diatur secara rutin setiap beberapa waktu.

## ENTRYPOINT INTRUCTION
Digunakan untuk menentukan executable file yang akan dijalankan. `ENTRYPOINT` erat kaitannya dengan instruksi `CMD`, saat kita menjalankan instruksi `CMD` secara otomatis akan menggunakan `ENTRYPOINT`.

## Multi Stage Build

Docker memiliki fitur Multi Stage Build, dimana dalam `Dockerfile` bisa membuat beberapa
Build Stage atau tahapan build. Di awal build biasanya kita menggunakan instruksi `FROM`, dan di dalam
`Dockerfile`, kita bisa menggunakan beberapa instruksi `FROM`. Setiap Instruksi `FROM`, artinya itu adalah build stage. Build stage terakhir adalah build stage yang akan dijadikan sebagai Image. Kita bisa memanfaatkan Docker build stage ini untuk melakukan proses kompilasi kode
program `Go-Lang` kita.

- Build `Dockerfile`.
  ```sh
  docker build -t devinwinando/multi-stage-build "Dockerfile/14. Multi Stage Build"
  ```
