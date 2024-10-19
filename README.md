# Task 3 : Priority Preemptive Scheduling
## Description
Proyek ini menggunakan sistem operasi real-time (RTOS) dengan penjadwalan preemptive berbasis prioritas pada mikrokontroler STM32 untuk mengelola dua tugas, yaitu mengendalikan LED. Tugas dengan prioritas lebih tinggi dapat mengganggu tugas dengan prioritas lebih rendah. Tugas ini menunjukkan cara kerja RTOS, di mana tugas dengan prioritas lebih tinggi selalu dijalankan terlebih dahulu, sedangkan tugas dengan prioritas lebih rendah dijalankan ketika tidak ada tugas yang lebih penting. Disini kami mengontrol led menggunakan GPIO pin PA0, PA1, PA4, dan PA5
### Project
![Gambar Rangkaian](https://github.com/user-attachments/assets/dd41768c-a888-478a-a331-67af3ea452d1)
### IOC PIN
![Pin IOC](https://github.com/user-attachments/assets/7e0124f6-7b3d-4bbf-b9da-c8f4b6155f41)

Project ini mengimplementasikan sebuah sistem RTOS (Real-Time Operating System) pada mikrokontroler STM32 yang mengontrol dua LED (hijau dan merah) menggunakan FreeRTOS. Ada tiga task utama dalam sistem ini, yaitu:
- defaultTask: Task ini adalah task default tanpa fungsi spesifik dan hanya berfungsi sebagai loop tak terbatas yang memberikan waktu tunda (delay) kecil secara berkelanjutan.
- GreenLEDTask: Task ini bertanggung jawab untuk mengontrol LED hijau. Task ini menyalakan LED hijau sebanyak 80 kali dengan pola nyala-mati dengan jeda 25ms. Setelah itu, task berhenti (osDelay) selama 6000ms (6 detik) sebelum mengulang proses.
- RedLEDTask: Task ini memiliki prioritas lebih tinggi dibandingkan dengan GreenLEDTask dan bertanggung jawab untuk mengontrol LED merah. LED merah akan menyala sebanyak 10 kali dengan pola nyala-mati yang sama, yaitu dengan jeda 25ms, dan berhenti selama 1500ms (1,5 detik) sebelum mengulang proses.

Hubungan Antar Task:
Karena RedLEDTask memiliki prioritas lebih tinggi, ketika dijalankan, task ini akan menghentikan sementara GreenLEDTask hingga selesai, yang disebut preemption.
Setelah RedLEDTask selesai, penjadwal RTOS akan kembali menjalankan GreenLEDTask. Jika RedLEDTask membutuhkan kembali CPU saat GreenLEDTask berjalan, sistem akan kembali memprioritaskan RedLEDTask.
Dengan ini, setiap task dijalankan berdasarkan prioritasnya, memungkinkan multitasking dan pengaturan sumber daya CPU yang efisien.
## Demo Task 3
https://github.com/user-attachments/assets/bc5f28d9-9195-4508-95d1-0561abab2c50
## Author
- Wildan Faizin (3222600011) 
- Dhanang Fadhila Trisnandi (3222600015)
