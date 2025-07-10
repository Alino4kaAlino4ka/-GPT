
# News Headline Generator with Russian GPT
# Генератор заголовков новостей на основе GPT


[![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](https://colab.research.google.com/drive/1RQkf73RxAjsxBHaLeQUqWb0tgfLZ6myO?usp=sharing)

Модель для автоматической генерации заголовков новостей на русском языке, основанная на архитектуре GPT. Проект выполнен в рамках учебного задания по дообучению языковых моделей.

## Особенности

- 🚀 Дообученная модель **rugpt3small** от Sberbank AI
- 📰 Работает с новостными текстами любого объема
- ✍️ Генерирует краткие, информативные заголовки
- 🔍 Автоматическая проверка релевантности заголовков
- ⚡ Оптимизировано для работы в Google Colab

## Технологии

- Python 3.10+
- Transformers 4.30+
- PyTorch 2.0+
- Datasets 2.12+
- Pandas 1.5+

## Установка

1. Клонируйте репозиторий:
```bash
git clone https://github.com/yourusername/news-headline-generator.git
cd news-headline-generator
```

2. Установите зависимости:
```bash
pip install -r requirements.txt
```

## Использование

### Быстрый старт в Colab
Откройте [ноутбук]([https://colab.research.google.com/github/yourusername/reponame/blob/main/news_headline_generator.ipynb](https://colab.research.google.com/drive/1RQkf73RxAjsxBHaLeQUqWb0tgfLZ6myO?usp=sharing)) и выполните все ячейки.

### Генерация заголовков
```python
from generator import NewsHeadlineGenerator

# Инициализация генератора
generator = NewsHeadlineGenerator()

# Пример текста новости
news_text = "Защитник сборной России по хоккею Андрей Марков принес победу..."

# Генерация заголовка
headline = generator.generate_headline(news_text)
print(f"Заголовок: {headline}")
```

### Результат
```
Заголовок: Андрей Марков принес победу "Монреалю" в матче НХЛ
```

## Датасет
Использован датасет [Lenta.ru News Corpus](https://www.kaggle.com/datasets/yutkin/corpus-of-russian-news-articles-from-lenta) с Kaggle:
- 800,970 новостных статей
- Период: 1999-2019 гг.
- Колонки: заголовок, текст, тема, дата

## Архитектура решения
1. **Предобработка данных**:
   - Очистка текстов
   - Формирование пар "текст-заголовок"
   - Токенизация

2. **Модель**:
   - Основа: rugpt3small (355M параметров)
   - Дообучение: 3 эпохи
   - Оптимизатор: AdamW

3. **Генерация**:
   - Beam search (num_beams=5)
   - Контроль повторов (no_repeat_ngram_size=2)
   - Температура: 0.7

## Примеры работы
| Текст новости | Сгенерированный заголовок |
|---------------|--------------------------|
| Центробанк повысил ключевую ставку до 8.5%... | ЦБ повысил ключевую ставку до 8.5% годовых |
| В Москве прошел митинг в поддержку эко-инициатив... | В столице состоялся митинг за экологию |

## Ограничения
- Максимальная длина текста: 1024 токена
- Лучше работает с новостями >200 символов
- Может пропускать второстепенные детали

## Лицензия
MIT License

## Контакты
Алина Грибанова - https://t.me/Alino4kaGribavova
```
 
