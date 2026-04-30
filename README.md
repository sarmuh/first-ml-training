# 🏠 Toshkent Uylar Narxi Bashorati

> Toshkent shahridagi uylar narxini bashorat qilish uchun ma'lumotlarni tahlil qilish va ML modeli yaratish loyihasi

---

## 📊 Loyiha Holati

![Status](https://img.shields.io/badge/Status-🚀%20Learning-brightgreen?style=for-the-badge)
![Progress](https://img.shields.io/badge/Progress-10%25%20EDA%20Completed-blue?style=for-the-badge)
![Dataset](https://img.shields.io/badge/Dataset-✅%20Loaded-success?style=for-the-badge)
![Python](https://img.shields.io/badge/Python-3.8+-blue?style=for-the-badge&logo=python&logoColor=white)

---

## 🎯 Loyiha Maqsadi

**Maqsad:** Toshkent shahridagi uylar narxini bashorat qilish uchun sifatli machine learning modeli yaratish

**Ma'lumotlar Manbai:** Toshkent uy bozorining real ma'lumotlari (Excel format)

---

## ✅ Bajarilgan Ishlar

### 📥 1-BOSQICH: Ma'lumotlarni Yuklash va Tanishish
- ✨ Excel fayldan ma'lumotlarni yuklash (`Toshkent_houses.xlsx`)
- 📋 Dataset tuzilmasini o'rganish (shape, columns)
- 📝 Ustunlar ta'rifini yaratish

### 🔍 2-BOSQICH: Tanloviy Tahlil (EDA)
- 📊 **Asosiy Statistika:** describe() - o'rtacha, min, max qiymatlar
- 🎯 **Null Qiymatlarni Tekshirish:** isna().sum() bilan bo'sh joylari aniqlash
- 🔗 **Korrelyatsion Tahlil:** feature va price o'rtasidagi bog'lanishni o'rganish
- 🗑️ **Ma'lumotlarni Tozalash:** address ustunini olib tashlash (1 satr = 1 manzil)

### 📈 3-BOSQICH: Ma'lumotlarni Vizualizatsiya
- 📊 **Histogramlar:** Barcha numeric feature lar uchun taqsimot
- 🎨 **Scatter Plot:** Joylashgan joyning xaritasida narx taqsimoti
- 📶 **Bar Plot:** Qavatlar bo'yicha o'rtacha narx
- 🔥 **Heatmap:** Korrelyatsion matritsani vizualizatsiya
- 📐 **Pairplot:** Feature va price o'rtasidagi bog'lanish

---

## 📁 Loyiha Tuzilmasi

```
first-ml-training/
├── 📄 README.md                          # Loyiha haqida ma'lumot
├── 📊 data/
│   ├── raw/
│   │   └── Toshkent_houses.xlsx          # Xom ma'lumotlar
│   └── processed/                        # Qayta ishlangan ma'lumotlar
├── 🤖 models/                            # O'qitilgan ML modellar
└── 📓 notebooks/
    └── 01_data_info.ipynb                # EDA Jupyter notebook
```

---

## 🛠 Foydalanilgan Texnologiyalar

![Python](https://img.shields.io/badge/python-3670A0?style=for-the-badge&logo=python&logoColor=ffdd54)
![Pandas](https://img.shields.io/badge/pandas-%23150458.svg?style=for-the-badge&logo=pandas&logoColor=white)
![NumPy](https://img.shields.io/badge/numpy-%23013243.svg?style=for-the-badge&logo=numpy&logoColor=white)
![Matplotlib](https://img.shields.io/badge/Matplotlib-%23ffffff.svg?style=for-the-badge&logo=Matplotlib&logoColor=black)
![Seaborn](https://img.shields.io/badge/Seaborn-blue?style=for-the-badge)
![Scikit-Learn](https://img.shields.io/badge/scikit--learn-%23F7931E.svg?style=for-the-badge&logo=scikit-learn&logoColor=white)

---

## 📊 Dataset Haqida Ma'lumot

| Parametr | Qiymat |
|----------|--------|
| **Ustunlar soni** | 7 |
| **Ma'lumot turlari** | String, Integer, Float |
| **Null qiymatlar** | Yo'q |
| **Manzil** | Toshkent shahri |
| **Uy turlari** | Barcha turlari (tilakli, ko'p qavatli) |

---

## 🔑 Asosiy O'zgaruvchilar

| O'zgaruvchi | Ta'rifi |
|-------------|---------|
| **location** | Sotilayotgan uy manzili |
| **district** | Uy joylashgan tuman |
| **rooms** | Xonalar soni |
| **size** | Uy maydoni (kv.m) |
| **level** | Uy joylashgan qavat |
| **max_levels** | Ja'mi qavatlar soni |
| **price** | Uy narxi (maqsad o'zgaruvchisi) |

---

## 🚀 Keyingi Bosqichlar

- [ ] Model tanlovni boshlash (Linear Regression, Random Forest)
- [ ] Feature Engineering qilish
- [ ] Model o'qitish va tekshirish
- [ ] Xatolarni tahlil qilish (MAE, RMSE, R²)
- [ ] Eng yaxshi modelni joylashtirish

---

## 📝 Qayd

*Loyiha tayyorlash jarayonida: Ma'lumotlarni tahlil qilish → Modelni o'qitish → Bashorat qilish*
