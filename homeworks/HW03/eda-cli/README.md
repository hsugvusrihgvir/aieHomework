# S03 – eda_cli: мини-EDA для CSV

Небольшое CLI-приложение для базового анализа CSV-файлов.
Используется в рамках Семинара 03 курса «Инженерия ИИ».

## Требования

- Python 3.11+
- [uv](https://docs.astral.sh/uv/) установлен в систему

## Инициализация проекта

В корне проекта (S03):

```bash
uv sync
```

## Запуск CLI

### Краткий обзор

```bash
uv run eda-cli overview data/example.csv
```

Параметры:

- `--sep` – разделитель (по умолчанию `,`);
- `--encoding` – кодировка (по умолчанию `utf-8`).

### Полный EDA-отчёт

```bash
uv run eda-cli report data/example.csv --out-dir reports
```

Новые параметры `report`:

- `--max-hist-columns` – сколько числовых колонок включать в набор гистограмм.
- `--top-k-categories` – сколько top-значений выводить для категориальных признаков.
- `--title` – заголовок отчёта (первая строка `# ...` в `report.md`).
- `--min-missing-share` – порог доли пропусков: колонки с `missing_share >= порога` попадают в список «проблемных» в `report.md`.

Пример запуска с новыми опциями:

```bash
uv run eda-cli report data/example.csv --out-dir reports_example --title "Отчёт по example" --max-hist-columns 8 --top-k-categories 7 --min-missing-share 0.1
```

## Тесты

```bash
uv run pytest -q
```
