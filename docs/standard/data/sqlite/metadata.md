---
title: Metadane
ms.date: 12/13/2019
description: Dowiedz się, jak pobrać metadane dotyczące bazy danych.
ms.openlocfilehash: b2f2704a748627d9943943fa2fa7b1b7e9f3007f
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447196"
---
# <a name="metadata"></a>Metadane

Istnieją dwa interfejsy API do pobierania metadanych w ADO.NET. Jeden pobiera metadane dotyczące wyników zapytania. Pozostałe pobiera metadane dotyczące schematu bazy danych.

## <a name="query-result-metadata"></a>Metadane wyników zapytania

Metadane dotyczące wyników zapytania można pobrać przy użyciu <xref:Microsoft.Data.Sqlite.SqliteDataReader.GetSchemaTable%2A> metody w. `SqliteDataReader` Zwrócone <xref:System.Data.DataTable> elementy zawierają następujące kolumny:

| Kolumna             | Typ    | Opis                                                               |
| ------------------ | ------- | ------------------------------------------------------------------------- |
| `AllowDBNull`      | Wartość logiczna | Prawda, jeśli kolumna pierwotna może mieć wartość NULL.                                    |
| `BaseCatalogName`  | Ciąg  | Nazwa bazy danych kolumny źródłowej. Zawsze wartość NULL dla wyrażeń.    |
| `BaseColumnName`   | Ciąg  | Niealiasowa nazwa kolumny źródła. Zawsze wartość NULL dla wyrażeń.    |
| `BaseSchemaName`   | Ciąg  | Zawsze wartość NULL. SQLite nie obsługuje schematów.                              |
| `BaseServerName`   | Ciąg  | Ścieżka do pliku bazy danych określona w parametrach połączenia.         |
| `BaseTableName`    | Ciąg  | Nazwa tabeli kolumny pierwotnej. Zawsze wartość NULL dla wyrażeń.       |
| `ColumnName`       | Ciąg  | Nazwa lub alias kolumny w zestawie wyników.                        |
| `ColumnOrdinal`    | Int32   | Numer porządkowy kolumny w zestawie wyników.                              |
| `ColumnSize`       | Int32   | Zawsze-1. Może to ulec zmianie w przyszłych wersjach `Microsoft.Data.Sqlite`programu.   |
| `DataType`         | Typ    | Domyślny typ danych platformy .NET dla kolumny.                                 |
| `DataTypeName`     | Ciąg  | Typ danych programu SQLite w kolumnie.                                       |
| `IsAliased`        | Wartość logiczna | True, jeśli nazwa kolumny jest aliasem w zestawie wyników.                     |
| `IsAutoIncrement`  | Wartość logiczna | Ma wartość true, jeśli kolumna pierwotna została utworzona za pomocą słowa kluczowego AUTOINCREMENT.     |
| `IsExpression`     | Wartość logiczna | Wartość true, jeśli kolumna pochodzi z wyrażenia w zapytaniu.            |
| `IsKey`            | Wartość logiczna | Wartość true, jeśli kolumna pierwotna jest częścią klucza podstawowego.                     |
| `IsUnique`         | Wartość logiczna | Ma wartość true, jeśli kolumna pierwotna jest UNIKATOWa.                                      |
| `NumericPrecision` | Int16   | Zawsze wartość NULL. Może to ulec zmianie w przyszłych wersjach `Microsoft.Data.Sqlite`programu. |
| `NumericScale`     | Int16   | Zawsze wartość NULL. Może to ulec zmianie w przyszłych wersjach `Microsoft.Data.Sqlite`programu. |

Poniższy przykład pokazuje, jak używać `GetSchemaTable` do tworzenia ciągu debugowania, który pokazuje metadane dotyczące wyniku:

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/ResultMetadataSample/Program.cs?name=snippet_ResultMetadata)]

Na przykład to zapytanie wygenerowało następujący ciąg debugowania:

```sql
SELECT id AS post_id,
       title,
       body,
       random() AS random
FROM post
```

```output
post.id AS post_id INTEGER PRIMARY KEY AUTOINCREMENT
post.title TEXT NOT NULL UNIQUE
post.body TEXT
(expression) AS random BLOB
```

## <a name="schema-metadata"></a>Metadane schematu

Microsoft. Data. sqlite nie implementuje metody GetSchema na DbConnection. Zamiast tego można wykonywać zapytania bezpośrednio dotyczące informacji o schemacie, korzystając z tabeli [sqlite_master](https://www.sqlite.org/fileformat.html#storage_of_the_sql_database_schema) i instrukcji pragma, takich jak [TABLE_INFO](https://www.sqlite.org/pragma.html#pragma_table_info) i [foreign_key_list](https://www.sqlite.org/pragma.html#pragma_foreign_key_list).

Na przykład to zapytanie spowoduje pobranie metadanych dotyczących wszystkich kolumn w bazie danych.

```sql
SELECT t.name AS tbl_name, c.name, c.type, c.notnull, c.dflt_value, c.pk
FROM sqlite_master AS t,
     pragma_table_info(t.name) AS c
WHERE t.type = 'table';
```

## <a name="see-also"></a>Zobacz też

* [Magazyn SQL Database schematu](https://www.sqlite.org/fileformat.html#storage_of_the_sql_database_schema)
* [PRAGMa — instrukcje](https://www.sqlite.org/pragma.html)
* [Typy danych](types.md)
