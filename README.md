# Таблица соответствий пневматики: чужой код → код WAALPC

Открытая таблица подбора аналогов промышленной пневматики: код изделия другого производителя (Festo, SMC, Camozzi, AirTAC, Parker, Norgren и др.) → код изделия WAALPC. Всего 78701 проверенных соответствий, 34 производителей.

Источник: [corneta.tech — подбор аналогов пневматики](https://corneta.tech/analog/) ([corneta.tech](https://corneta.tech/)). Таблица выгружена 01.11.2026 из рабочей базы сайта; в выгрузку попали только соответствия, прошедшие проверку.

## Столбцы

| Столбец | Смысл |
|---|---|
| brand | производитель чужого изделия |
| alien_code | код чужого изделия, как он указан у производителя |
| waalpc_code | код изделия WAALPC |
| level | уровень соответствия (см. ниже) |
| page_url | страница на corneta.tech/analog/ с описанием подбора; пусто, если отдельной страницы нет |

## Уровни

- `drop_in` — полное соответствие: изделие WAALPC ставится вместо чужого без переделки.
- `near` — близкое соответствие: основные параметры совпадают, но есть отличие, которое нужно учесть при замене (например, резьба портов: у чужого изделия PT/Rc, у нашего G). Отличие указано на странице подбора.

Перед заменой сверяйте параметры по паспорту изделия и по странице на сайте. Ряд ISO в таблицу не включён.

## Файлы по производителям

| Производитель | Файл | Строк |
|---|---|---|
| SMC | [smc.csv](data/smc.csv) | 18932 |
| AirTAC | [airtac.csv](data/airtac.csv) | 16073 |
| Festo | [festo.csv](data/festo.csv) | 8826 |
| SNS | [sns.csv](data/sns.csv) | 5352 |
| XCPC | [xcpc.csv](data/xcpc.csv) | 4529 |
| Camozzi | [camozzi.csv](data/camozzi.csv) | 3644 |
| Mindman | [mindman.csv](data/mindman.csv) | 3197 |
| STNC | [stnc.csv](data/stnc.csv) | 3165 |
| Pneumax | [pneumax.csv](data/pneumax.csv) | 2705 |
| CHELIC | [chelic.csv](data/chelic.csv) | 2105 |
| Norgren | [norgren.csv](data/norgren.csv) | 1601 |
| Parker | [parker.csv](data/parker.csv) | 1512 |
| E.MC | [e-mc.csv](data/e-mc.csv) | 1105 |
| Metal Work | [metal-work.csv](data/metal-work.csv) | 1050 |
| CKD | [ckd.csv](data/ckd.csv) | 993 |
| Aignep | [aignep.csv](data/aignep.csv) | 911 |
| Univer | [univer.csv](data/univer.csv) | 891 |
| Legris | [legris.csv](data/legris.csv) | 551 |
| AVENTICS | [aventics.csv](data/aventics.csv) | 545 |
| Bosch | [bosch.csv](data/bosch.csv) | 503 |
| PISCO | [pisco.csv](data/pisco.csv) | 398 |
| Burkert | [burkert.csv](data/burkert.csv) | 55 |
| ASCO | [asco.csv](data/asco.csv) | 16 |
| Pemaks | [pemaks.csv](data/pemaks.csv) | 11 |
| Goyen | [goyen.csv](data/goyen.csv) | 8 |
| NBPT | [nbpt.csv](data/nbpt.csv) | 7 |
| FESCOLO | [fescolo.csv](data/fescolo.csv) | 5 |
| ZITA | [zita.csv](data/zita.csv) | 3 |
| OLK | [olk.csv](data/olk.csv) | 2 |
| Rotork | [rotork.csv](data/rotork.csv) | 2 |
| ASCO Joucomatic | [asco-joucomatic.csv](data/asco-joucomatic.csv) | 1 |
| Aventics | [aventics.csv](data/aventics.csv) | 1 |
| Findeva | [findeva.csv](data/findeva.csv) | 1 |
| SXPC | [sxpc.csv](data/sxpc.csv) | 1 |

Цены и закупочные данные в таблицу не входят.

## Лицензия

[CC BY 4.0](https://creativecommons.org/licenses/by/4.0/deed.ru): можно использовать, копировать и изменять с указанием источника — «corneta.tech — подбор аналогов пневматики», https://corneta.tech/analog/.

---

## English summary

Open cross-reference table for industrial pneumatics: third-party part number (Festo, SMC, Camozzi, AirTAC, Parker, Norgren, etc.) → WAALPC part number. 78701 verified mappings, 34 manufacturers, one CSV per brand in `data/`. Columns: `brand`, `alien_code`, `waalpc_code`, `level`, `page_url`. Levels: `drop_in` = direct replacement; `near` = close match with a difference to consider (e.g. port thread PT/Rc vs G). No prices. Always check datasheets before substitution.

License: CC BY 4.0. Attribution: "corneta.tech — подбор аналогов пневматики", https://corneta.tech/analog/ (site: https://corneta.tech/).
