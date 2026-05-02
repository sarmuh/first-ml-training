# Tashkent House Price Prediction

Bu loyiha Toshkent shahridagi uy narxlarini tahlil qilish, ma'lumotlarni tozalash va machine learning pipeline tayyorlash uchun yaratilgan o'quv loyihadir.

## Loyiha holati

Hozir bajarilgan ishlar:

- raw Excel dataset yuklandi va tahlil qilindi;
- keraksiz `address` ustuni olib tashlandi;
- narx va maydon bo'yicha outlier qiymatlar filter qilindi;
- tozalangan dataset `data/processed/tashkent_houses.csv` fayliga saqlandi;
- numeric va categorical ustunlar uchun preprocessing pipeline tayyorlandi;
- `ColumnTransformer` orqali `district` uchun OneHot encoding va numeric ustunlar uchun scaling ishlaydi;
- custom feature engineering qo'shildi: `room_size` va `distance_to_center`.

Keyingi asosiy qadam: tayyorlangan pipeline asosida regression modellarni train qilish va baholash.

## Papkalar tuzilishi

```text
first-ml-training/
|-- README.md
|-- data/
|   |-- raw/
|   |   `-- tashkent_houses.xlsx
|   `-- processed/
|       `-- tashkent_houses.csv
|-- models/
|   `-- .gitkeep
`-- notebooks/
    |-- 01_data_info.ipynb
    |-- 02_data_Preprocessing.ipynb
    `-- 03_data_training.ipynb
```

## Papkalar tavsifi

| Papka | Tavsif |
|---|---|
| `data/raw/` | Boshlang'ich, o'zgartirilmagan dataset. Hozir: `tashkent_houses.xlsx`. |
| `data/processed/` | Tozalangan va preprocessingdan o'tgan dataset. Hozir: `tashkent_houses.csv`. |
| `notebooks/` | Tahlil, preprocessing va training pipeline bo'yicha Jupyter notebooklar. |
| `models/` | Kelajakda train qilingan model fayllari saqlanadigan joy. Hozircha bo'sh. |

## Notebooklar

| Notebook | Vazifasi |
|---|---|
| `01_data_info.ipynb` | Datasetni yuklash, ustunlarni tushunish, EDA, visualizatsiya va boshlang'ich feature engineering. |
| `02_data_Preprocessing.ipynb` | `address` ustunini olib tashlash, outlier filter, train/test split, encoding, scaling va processed CSV saqlash. |
| `03_data_training.ipynb` | Processed CSV bilan ishlash, custom transformer, numeric/categorical pipeline va `ColumnTransformer` tayyorlash. |

## Dataset

Processed dataset haqida:

| Parameter | Qiymat |
|---|---:|
| Qatorlar soni | 7405 |
| Ustunlar soni | 8 |
| Target ustun | `price` |
| Categorical ustun | `district` |
| Numeric ustunlar | `rooms`, `size`, `level`, `max_levels`, `lat`, `lng` |

Ustunlar:

| Ustun | Tavsif |
|---|---|
| `district` | Uy joylashgan tuman |
| `rooms` | Xonalar soni |
| `size` | Uy maydoni, kvadrat metr |
| `level` | Uy joylashgan qavat |
| `max_levels` | Binodagi jami qavatlar soni |
| `price` | Uy narxi, target qiymat |
| `lat` | Latitude koordinata |
| `lng` | Longitude koordinata |

## Preprocessing jarayoni

Asosiy preprocessing qadamlari:

1. `data/raw/tashkent_houses.xlsx` fayli o'qiladi.
2. `address` ustuni olib tashlanadi.
3. Dataset `price <= 400000` va `size <= 350` shartlari bilan filter qilinadi.
4. Dataset train/test qismlarga ajratiladi.
5. `district` ustuni categorical feature sifatida encoding qilinadi.
6. Numeric ustunlardan yangi featurelar yaratiladi:
   - `room_size = size / rooms`
   - `distance_to_center` - Toshkent markazigacha Haversine formulasi bo'yicha masofa
7. Numeric featurelar `StandardScaler` orqali scale qilinadi.
8. Tozalangan dataset CSV formatida saqlanadi.

## Training pipeline

`03_data_training.ipynb` ichida quyidagi pipeline ishlatiladi:

```python
num_pipeline = Pipeline([
    ('custom_features_adder', CustomFeaturesAdder()),
    ('std_scaler', StandardScaler())
])

full_pipeline = ColumnTransformer([
    ('num', num_pipeline, numeric_attr),
    ('cat', OneHotEncoder(), categorical_attr)
])
```

Muhim eslatma: `CustomFeaturesAdder.transform()` ichida `X = np.asarray(X)` ishlatiladi. Bu kerak, chunki `ColumnTransformer` ba'zan `pandas.DataFrame` yuboradi, transformer esa `X[:, index]` kabi NumPy indekslashdan foydalanadi.

## Ishga tushirish

Kerakli kutubxonalar:

```bash
pip install numpy pandas matplotlib seaborn scikit-learn openpyxl jupyter
```

Notebooklarni quyidagi tartibda ishga tushirish tavsiya qilinadi:

1. `notebooks/01_data_info.ipynb`
2. `notebooks/02_data_Preprocessing.ipynb`
3. `notebooks/03_data_training.ipynb`

## Keyingi vazifalar

- regression model tanlash: Linear Regression, Decision Tree, Random Forest;
- train qilingan modelni MAE, RMSE va R2 metrikalari bilan baholash;
- eng yaxshi modelni `models/` papkasiga saqlash;
- prediction uchun alohida inference funksiyasi yoki notebook qo'shish.

