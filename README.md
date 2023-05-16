#   Room Security System
### _Kelompok A1 Sistem Siber Fisik-02_

Room Security System adalah alat keamanan ruangan yang dirancang dengan teknologi canggih dan dilengkapi dengan sensor gerak yaitu PIR Sensor Passive Infra Red) dan Sensor HC-SR04 untuk mengukur jarak yang terdeteksi oleh sensor PIR yang kemudian ditampilkan melalui 7 Segment MAX7219.

    Group A1:
        - Azzah Azkiyah Angeli Syahwa        - 2106731390
        - Cecilia Inez Reva Manurung          - 2106636994
        - Mikhael Morris Hapataran Siallagan  - 2106731491
        - Muhammad Cavan Naufal Azizi	      - 2106702730

## Features

-   [Introduction to the problem and the solution](#introduction-to-the-problem-and-the-solution)
-   [Hardware design and implementation details](#hardware-design-and-implementationdetails)
    -   [Schematic](#common-options)
-   [Software implementation details](#software-implementation-details)
    -   [Common Options](#common-options)
-   [Test results and performance evaluation](#test-results-and-performance-evaluation)
    -   [Test results and performance evaluation](#test-results-and-performance-evaluation)


## i. Introduction to the problem and the solution

Kejahatan merupakan sebuah tindakan yang tidak terpuji dan sangat merugikan korban. Semakin banyak kejahatan yang terjadi, semakin banyak pula kerugian yang akan terjadi pada pihak korban. Zaman yang semakin maju ini, tingkat kejahatan makin tinggi dan metodenya pun semakin canggih. Kita sendiri perlu melakukan antisipasi dan pengawasan terhadap properti milik kita dan diri kita sendiri untuk mencegah hal-hal yang tidak diinginkan. Pencegahan dini dapat dilakukan dimulai dari lingkungan sekitar, yaitu tempat tinggal kita. Kita perlu memperketat pengawasan dan penjagaan pada rumah atau tempat tinggal yang ditinggali. Oleh karena itu, kelompok kami membawa sebuah ide untuk membuat Room Security System.

Room Security System merupakan sebuah sistem pengaman ruangan yang dilengkapi dengan sensor gerak dan sensor jarak yang bertujuan untuk melakukan pengawasan terhadap celah-celah rawan pada rumah kita seperti pintu dan jendela. Alat ini akan mendeteksi gerakan pintu/jendela dengan menggunakan sensor dan jika sudah mencapai suatu kondisi tertentu akan mengaktifkan suara yang bersumber dari buzzer dan LED akan menyala yang menandakan tanda mencurigakan atau bahaya.

## ii. Hardware design and implementation details

Peralatan yang dibutuhkan untuk merangkai Room Security System :

![Arduino Uno AtMega328p](https://github.com/CavanNaufal/Proyek_Akhir_SSF_Kelompok_A1/assets/88528641/ce32f361-a6b4-462e-b747-a1c8d21ef533)
Sebagai 'otak' utama dalam mengatur semua sistem agar bisa berjalan.
- Sensor PIR : Melakukan deteksi terhadap gerakan yang terjadi di sekitarnya.
- Sensor HC-SR04 : Melakukan pengukuran jarak suatu objek terhadap security system.
- LED : LED akan menyala sebagai penanda jika terjadi bahaya.
- Module Buzzer : Buzzer akan berbunyi jika terjadi bahaya.
- Breadbroad : Sebagai media untuk merangkai semua komponen menjadi satu bagian.
- Jumper : Sebagai kabel penghubung antar komponen.
- Baterai/Catu daya : Sebagai sumber daya penggerak Room Security System ini.
- Seven Segment Module : Menampilkan jarak antara sebuah objek dengan sensor pada sistem ini.

Langkah-langkah merangkainya :

## iii. Software implementation details

Program ini ditulis dalam bahasa assembly untuk menghubungkan sensor PIR, sensor jarak HC-SR04 dan LED seven-segment MAX7219 dalam mikrokontroler ATMega328P. Program ini menggunakan protokol komunikasi serial synchronous yaitu SPI (Serial Peripheral Interface) untuk berkomunikasi dengan MAX7219 dan menghitung jarak yang diukur sensor HC-SR04 dengan mengukur lebar pulsa dari sinyal echo. Program dimulai dengan mengatur port input atau output. Port D dikonfigurasi sebagai output untuk LED merah dan buzzer yang terhubung, dan pin A0 (PC0) dikonfigurasi sebagai input untuk button. Pin PB0 dan PB1 dikonfigurasi sebagai pin input dan output untuk sensor HC-SR04. 

Pada loop utama, program mengirimkan high pulse 10us ke sensor HC-SR04 untuk memulai pengukuran jarak. Kemudian menghitung lebar pulsa dari sinyal echo dengan subroutine echo_PW, yang menggunakan Timer1 (normal mode). Program kemudian mengubah lebar pulse terukur menjadi nilai desimal dan menampilkannya pada MAX7219 menggunakan subroutine MAX7219_disp_text. Subroutine MAX7219_disp_text akan menampilkan string text “d” pada 2 digit pertama. Jika tombol yang terhubung ke pin A0 ditekan, LED dan buzzer yang terhubung ke port D akan menyala sebentar, dan kemudian mati. 

Subroutine SPI_MAX7219_init mengatur SPI untuk berkomunikasi dengan MAX7219 dengan menyalakan pin MOSI (Master In Slave Out), SCK (clock signal) dan SS sebagai output dengan menuliskan bit 1 ke DDRB dan mengaktifkan SPI pada bit pertama (SPE). Subroutine send_bytes digunakan untuk mengatur intensitas segment LED dengan nilai 8 dan mengatur scan limit dengan nilai 7 yang artinya menampilkan 8 digit pada MAX7219 dan menyalakan MAX7219.


## iv. Test results and performance evaluation
