# Pollution Data Preprocessing with TensorFlow Transform (TFT)

## 📌 Project Overview

This project demonstrates how to preprocess pollution data using **TensorFlow Transform (TFT)** — a library for preprocessing data with TensorFlow. The dataset includes daily pollution metrics such as `pm10`, `no2`, `so2`, and `soot`, which are standardized and normalized using `tft` to prepare for model training.

## 📊 Dataset Description

The dataset (`pollution_small.csv`) includes:

* `Date`: Date of measurement (excluded during transformation)
* `pm10`, `no2`, `so2`, `soot`: Pollution readings

These features are numeric and need to be scaled or normalized before training ML models.

---

## ⚙️ Techniques Used

* **TensorFlow Transform (TFT)** for scalable preprocessing
* **Apache Beam** as the data processing backend
* **Feature engineering**: Normalization and scaling
* **Schema definition** using `tf.io.FixedLenFeature`
* **Temp directory** handling with Python's `tempfile`

### ✨ Preprocessing Techniques Applied

| Feature      | Technique             | Function                     |
| ------------ | --------------------- | ---------------------------- |
| `no2`, `so2` | Mean normalization    | `no2 - tft.mean(no2)`        |
| `pm10`       | 0–1 MinMax scaling    | `tft.scale_to_0_1(pm10)`     |
| `soot`       | Custom MinMax scaling | `tft.scale_by_min_max(soot)` |

---

## 🔁 Sample Output

```
Raw:        {'pm10': 25.75, 'no2': 21.59, 'so2': 11.19, 'soot': 9.89}
Transformed: {'no2_normalized': -7.26, 'pm10_normalized': 0.12, 'so2_normalized': -4.29, 'soot_normalized': 0.05}

Raw:        {'pm10': 19.6, 'no2': 17.79, 'so2': 10.34, 'soot': 9.42}
Transformed: {'no2_normalized': -11.08, 'pm10_normalized': 0.09, 'so2_normalized': -4.33, 'soot_normalized': 0.03}
```

The transformed values are the result of standardizing and scaling to help machine learning models learn more effectively.

---

## 🧠 Purpose of This Course / Module

This hands-on mini-project is part of a broader **ML pipeline engineering or MLOps course**. The goal is to:

* Learn **data transformation techniques at scale**
* Understand **feature engineering using TensorFlow Transform**
* Practice building a **reproducible preprocessing pipeline**
* Prepare inputs for **TensorFlow model training**

---

## 🚧 Challenges Faced

* 🖐️ Defining correct `feature_spec` for schema
* 📉 Understanding how TFT operations like `tft.mean()` work internally
* 🏗 Integrating with `Beam`'s pipeline syntax
* 💥 Debugging when transformed outputs seemed too similar to inputs
* 🧪 Ensuring transformations are **consistent across training and serving**

---

## 🧑‍💻 Responsibilities and What I Did

* ✅ Loaded and cleaned pollution dataset
* ✅ Defined metadata schema and conversion logic
* ✅ Built a `preprocessing_fn` for normalized/scaled features
* ✅ Ran transformations using `tft_beam.AnalyzeAndTransformDataset`
* ✅ Printed raw vs transformed examples for debugging and verification
* ✅ Documented and structured pipeline logic




---

## 📟 Learn More

* [TensorFlow Transform Docs](https://www.tensorflow.org/tfx/transform/get_started)
* [Apache Beam Programming Guide](https://beam.apache.org/documentation/programming-guide/)
