# Customer Segmentation Streaming

System do przetwarzania danych strumieniowych z wykorzystaniem Apache Spark i segmentacji klientów na podstawie zachowań zakupowych.

## Opis działania

Strumień danych wejściowych pochodzi z plików JSON generowanych przez skrypt `generator.py`.

Każde zdarzenie zawiera informacje o:
- użytkowniku (`user_id`)
- rodzaju zdarzenia (`event_type`: `view`, `cart`, `purchase`)
- czasie (`timestamp`)
- produkcie (`product_id`), kategorii (`category`) i cenie (`price`)

## Logika segmentacji

Na podstawie sekwencji zdarzeń użytkownika w 5-minutowym oknie czasowym:

- Jeśli wystąpiło `purchase` → **Buyer**
- Jeśli było `cart`, ale brak `purchase` → **Cart abandoner**
- Jeśli tylko `view` → **Lurker**

## Uruchamianie

1. Uruchom generator danych:

```bash
python generator.py
```

2. Otwórz notebook `customer_segmentation.ipynb` i uruchom go krok po kroku w JupyterLab.

## Wymagania

- Python 3.10
- Apache Spark
- PySpark
- Jupyter Notebook

## Struktura projektu

```
.
├── generator.py                 # Generator danych strumieniowych (JSON)
├── customer_segmentation.ipynb # Notebook z analizą i segmentacją klientów
└── README.md
```

## Przykładowy rekord wejściowy (JSON)

```json
{
  "user_id": "u45",
  "event_type": "purchase",
  "timestamp": "2025-05-14T12:34:00Z",
  "product_id": "p101",
  "category": "electronics",
  "price": 299.99
}
```


