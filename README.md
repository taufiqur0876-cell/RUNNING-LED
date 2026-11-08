# Running LED (RUNNING_LED_FF)

Proyek PCB **running LED** (lampu LED berjalan) yang dirancang di **KiCad**. Sinyal clock dihasilkan oleh timer **NE555** (mode astable) lalu diteruskan ke counter **CD4017** untuk menggeser nyala LED satu per satu.

## Status

🚧 Prototipe — desain skematik dan layout PCB sudah dibuat, tahap pengujian dan debugging rangkaian.

## Cara Kerja Singkat

1. **Regulator tegangan** (LD1117S50) menurunkan tegangan masukan (VIN) menjadi VCC 5 V untuk seluruh rangkaian.
2. **NE555** bekerja sebagai osilator astable. Frekuensinya ditentukan oleh resistor, dioda 1N4148, dan kapasitor C6 pada jalur DIS/THR/TR. Keluarannya (`555_OUT`) menjadi sinyal clock.
3. **CD4017** menerima clock di pin CLK, lalu menggeser keluaran aktif (Q0 ... Q9) satu langkah setiap pulsa sehingga LED menyala bergantian.
4. **LED indikator** menunjukkan kondisi catu daya dan keluaran 555.
5. Terdapat juga rangkaian **astable multivibrator** dari dua transistor MMBT3904 dengan dua LED yang berkedip bergantian.

## Komponen Utama

| Komponen | Fungsi |
|---|---|
| LD1117S50 | Regulator tegangan 5 V |
| NE555 | Pembangkit clock (astable) |
| CD4017 | Counter dekade, penggeser LED |
| MMBT3904 (x2) | Astable multivibrator transistor |
| 1N4148 (x2) | Pengatur siklus kerja (duty cycle) 555 |
| LED + resistor 220 ohm | Indikator dan LED berjalan |

## Gambar

### Skematik

![Skematik Running LED](images/schematic.png)

### Layout PCB

![Layout PCB Running LED](images/pcb-layout.png)

## Struktur Repositori

```
.
├── README.md
├── images/
│   ├── schematic.png
│   └── pcb-layout.png
└── RUNNING_LED_FF.kicad_pcb   # file desain KiCad
```

## Cara Membuka

1. Pasang [KiCad](https://www.kicad.org/).
2. Buka file proyek (`.kicad_pro`) atau langsung `RUNNING_LED_FF.kicad_pcb`.

## Penulis

Taufiqur Rahman — Politeknik Elektronika Negeri Surabaya (PENS)
