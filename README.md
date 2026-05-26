# Disaster Tweets Classification

Проект по задаче бинарной классификации твитов из соревнования
[NLP with Disaster Tweets](https://www.kaggle.com/competitions/nlp-getting-started):
по тексту нужно определить, относится ли сообщение к реальной чрезвычайной ситуации.

В работе сравнили классический baseline на `TF-IDF + Logistic Regression` и
transformer-модель `DistilBERT`, вручную посмотрели сложные примеры и отдельно
проверили датасет на дубликаты и возможный leakage.

## Результаты

| Модель | F1 на локальной валидации |
|---|---:|
| TF-IDF + Logistic Regression | 0.8311 |
| DistilBERT | **0.8153** |

В `results/` также сохранен эксперимент с leakage audit. Полученное там
значение `F1 = 0.997` показывает влияние утечки в validation и не является
результатом модели.

## Файлы

- `code/` - ноутбуки с экспериментами;
- `data/` - train/test и файл ручной проверки примеров;
- `results/` - метрики и результаты leakage audit;
- `csv/` - submission-файлы;
- `nlp_article_long.pdf` - итоговый отчет.

Датасет содержит `7613` обучающих и `3263` тестовых твита.

<img width="60" height="59" alt="image" src="https://github.com/user-attachments/assets/7bb75019-3103-4c86-9373-ed9a1b30da5e" />
