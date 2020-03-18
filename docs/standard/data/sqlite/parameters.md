---
title: Parametry
ms.date: 12/13/2019
description: Dowiedz się, jak używać parametrów SQL.
ms.openlocfilehash: 1d2f818ad392a919faedd785394de28a9c6f56c3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400457"
---
# <a name="parameters"></a>Parametry

Parametry są używane do ochrony przed atakami iniekcji SQL. Zamiast konkretyzować dane wejściowe użytkownika z instrukcjami SQL, należy użyć parametrów, aby upewnić się, że dane wejściowe są zawsze traktowane jako wartość literału i nigdy nie są wykonywane. W SQLite parametry są zazwyczaj dozwolone w dowolnym miejscu literału jest dozwolone w instrukcjach SQL.

Parametry można poprzedzać `:` `@`jednymi `$`, lub .

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/HelloWorldSample/Program.cs?name=snippet_Parameter)]

Zobacz [Typy danych,](types.md) aby uzyskać szczegółowe informacje o sposobie zamapowania wartości .NET na wartości SQLite.

## <a name="truncation"></a>Obcinania

Właściwość <xref:Microsoft.Data.Sqlite.SqliteParameter.Size> służy do obcinania wartości TEXT i BLOB.

```csharp
// Truncate name to 30 characters
command.Parameters.AddWithValue("$name", name).Length = 30;
```

## <a name="alternative-types"></a>Typy alternatywne

Czasami możesz chcieć użyć alternatywnego typu SQLite. Należy to zrobić, ustawiając <xref:Microsoft.Data.Sqlite.SqliteParameter.SqliteType> właściwość.

Można użyć następujących mapowania typu alternatywnego. Aby uzyskać domyślne mapowania, zobacz [Typy danych](types.md).

| Wartość          | Typ sqlite | Uwagi          |
| -------------- | ---------- | ---------------- |
| Char           | Liczba całkowita    | UTF-16           |
| DateTime       | Rzeczywiste       | Wartość dnia juliańska |
| Datetimeoffset | Rzeczywiste       | Wartość dnia juliańska |
| Guid (identyfikator GUID)           | Obiekt blob       |                  |
| przedział_czasu       | Rzeczywiste       | W dniach          |

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/DateAndTimeSample/Program.cs?name=snippet_SqliteType)]

## <a name="output-parameters"></a>Parametry wyjściowe

SQLite nie obsługuje parametrów wyjściowych. Zamiast tego zwraca wartości w wynikach kwerendy.

## <a name="see-also"></a>Zobacz też

* [Typy danych](types.md)
