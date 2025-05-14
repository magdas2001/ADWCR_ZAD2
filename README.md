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

2. Otwórz `customer_segmentation.ipynb` i uruchom kod w JupyterLab.

## Wymagania

- Python 3.10
- Apache Spark
- PySpark
- Jupyter Notebook
