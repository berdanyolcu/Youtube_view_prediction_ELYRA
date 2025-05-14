# 🎬 YouTube View Prediction (Elyra Pipeline)

Bu proje, YouTube videolarının açıklama verilerine (metadata) bakarak kaç izlenme alacağını tahmin etmek için oluşturulmuş uçtan uca bir makine öğrenimi pipeline'ıdır. Elyra kullanılarak JupyterLab ortamında görsel olarak oluşturulmuş ve çalıştırılmıştır.

---

## 🚀 Pipeline Adımları

1. **01_data_ingestion.ipynb**  
   Ham verileri okur ve birleştirir.

2. **02_data_cleaning.ipynb**  
   Eksik verileri ve hatalı satırları temizler.

3. **03_feature_engineering.ipynb**  
   Yeni öznitelikler (feature) üretir (örneğin: like_ratio, comment_density vs.).

4. **04_eda_visualization.ipynb**  
   Görsel keşif analizi (EDA) yapar.

5. **05_model_training.ipynb**  
   Regresyon modeli eğitir, RMSE ve R² skorlarını hesaplar.

6. **app.py**  
   Eğitilen modeli yükleyip Flask ile bir REST API olarak yayınlar.

---

## 🧪 Örnek API Kullanımı

```bash
curl -X POST http://127.0.0.1:5000/predict \
-H "Content-Type: application/json" \
-d '{
  "title_length": 52,
  "tag_count": 5,
  "has_tags": 1,
  "like_ratio": 0.85,
  "comment_density": 0.002,
  "like_per_view": 0.08,
  "dislike_per_view": 0.01,
  "publish_hour": 14,
  "category_code": 10
}'
## 🧪 Yanit

{
  "predicted_views": 988228
}

