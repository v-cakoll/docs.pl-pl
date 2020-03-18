---
title: Parametry połączeń
ms.date: 12/13/2019
description: Obsługiwane słowa kluczowe i wartości ciągów połączeń.
ms.openlocfilehash: bb54d152bac62a86c2a49192cf678a745159164e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400450"
---
# <a name="connection-strings"></a>Parametry połączeń

Ciąg połączenia służy do określania sposobu łączenia się z bazą danych. Parametry połączenia w programie Microsoft.Data.Sqlite są zgodne ze standardową [składnią ADO.NET](../../../framework/data/adonet/connection-strings.md) jako oddzieloną średnikami listą słów kluczowych i wartości.

## <a name="keywords"></a>Słowa kluczowe

Z plikami microsoft.Data.sqlite można używać następujących słów kluczowych ciągu połączenia:

### <a name="data-source"></a>Źródło danych

Ścieżka do pliku bazy danych. *DataSource* (bez spacji) i *Nazwa pliku* są aliasami tego słowa kluczowego.

SQLite traktuje ścieżki względem bieżącego katalogu roboczego. Można również określić ścieżki bezwzględne.

Jeśli **jest pusta**, SQLite tworzy tymczasową bazę danych na dysku, która jest usuwana po zamknięciu połączenia.

Jeśli `:memory:`używana jest baza danych w pamięci. Aby uzyskać więcej informacji, zobacz [Bazy danych w pamięci](in-memory-databases.md).

Ścieżki rozpoczynające `|DataDirectory|` się od ciągu podstawienia są traktowane tak samo jak ścieżki względne. Jeśli jest ustawiona, ścieżki są dokonywane względem wartości właściwości domeny aplikacji DataDirectory.

To słowo kluczowe obsługuje również [nazwy plików URI](https://www.sqlite.org/uri.html).

### <a name="mode"></a>Tryb

Tryb połączenia.

| Wartość           | Opis                                                                                        |
| --------------- | -------------------------------------------------------------------------------------------------- |
| ReadWriteCreate (Tworzenie zapisu wuzw | Otwiera bazę danych do odczytu i zapisu i tworzy ją, jeśli nie istnieje. Domyślnie włączone. |
| Odczyt/zapis       | Otwiera bazę danych do odczytu i zapisu.                                                        |
| ReadOnly        | Otwiera bazę danych w trybie tylko do odczytu.                                                              |
| Memory (Pamięć)          | Otwiera bazę danych w pamięci.                                                                       |

### <a name="cache"></a>Pamięć podręczna

Tryb buforowania używany przez połączenie.

| Wartość   | Opis                                                                                    |
| ------- | ---------------------------------------------------------------------------------------------- |
| Domyślne | Używa trybu domyślnego podstawowej biblioteki SQLite. Domyślnie włączone.                   |
| Private | Każde połączenie używa prywatnej pamięci podręcznej.                                                          |
| Udostępnione  | Połączenia współużytkują pamięć podręczną. Ten tryb można zmienić zachowanie transakcji i blokowania tabeli. |

### <a name="password"></a>Hasło

Klucz szyfrowania. Po określeniu `PRAGMA key` jest wysyłany natychmiast po otwarciu połączenia.

> [!WARNING]
> Hasło nie ma wpływu, gdy szyfrowanie nie jest obsługiwane przez natywną bibliotekę SQLite.

### <a name="foreign-keys"></a>Klucze obce

Wartość wskazująca, czy włączyć ograniczenia klucza obcego.

| Wartość   | Opis
| ------- | --- |
| True    | Wysyła `PRAGMA foreign_keys = 1` natychmiast po otwarciu połączenia.
| False   | Wysyła `PRAGMA foreign_keys = 0` natychmiast po otwarciu połączenia.
| (pusty) | Nie wysyła `PRAGMA foreign_keys`. Domyślnie włączone. |

Nie ma potrzeby włączania kluczy obcych, jeśli, jak w e_sqlite3, SQLITE_DEFAULT_FOREIGN_KEYS został użyty do skompilowania natywnej biblioteki SQLite.

### <a name="recursive-triggers"></a>Wyzwalacze cykliczne

Wartość, która wskazuje, czy włączyć wyzwalacze cykliczne.

| Wartość | Opis                                                                 |
| ----- | --------------------------------------------------------------------------- |
| True  | Wysyła `PRAGMA recursive_triggers` natychmiast po otwarciu połączenia. |
| False | Nie wysyła `PRAGMA recursive_triggers`. Domyślnie włączone.              |

## <a name="connection-string-builder"></a>Konstruktor ciągów połączeń

Można użyć <xref:Microsoft.Data.Sqlite.SqliteConnectionStringBuilder> jako silnie typizony sposób tworzenia ciągów połączeń. Może być również używany do zapobiegania atakom iniekcji ciągu połączenia.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/EncryptionSample/Program.cs?name=snippet_ConnectionStringBuilder)]

## <a name="examples"></a>Przykłady

### <a name="basic"></a>Podstawowa (Basic)

Podstawowy ciąg połączenia z udostępnionej pamięci podręcznej dla poprawy współbieżności.

```ConnectionString
Data Source=Application.db;Cache=Shared
```

### <a name="encrypted"></a>Zaszyfrowane

Zaszyfrowana baza danych.

```ConnectionString
Data Source=Encrypted.db;Password=MyEncryptionKey
```

### <a name="read-only"></a>Tylko odczyt

Baza danych tylko do odczytu, która nie może być modyfikowana przez aplikację.

```ConnectionString
Data Source=Reference.db;Mode=ReadOnly
```

### <a name="in-memory"></a>W pamięci

Prywatna baza danych w pamięci.

```ConnectionString
Data Source=:memory:
```

### <a name="sharable-in-memory"></a>Sharable in-memory

Sharable, w pamięci bazy danych identyfikowane przez nazwę *Sharable*.

```ConnectionString
Data Source=Sharable;Mode=Memory;Cache=Shared
```

## <a name="see-also"></a>Zobacz też

* [Parametry połączenia w ADO.NET](../../../framework/data/adonet/connection-strings.md)
* [Bazy danych w pamięci](in-memory-databases.md)
* [Transakcje](transactions.md)
