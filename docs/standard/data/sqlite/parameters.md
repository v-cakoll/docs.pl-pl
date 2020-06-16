---
title: Parametry
ms.date: 12/13/2019
description: Dowiedz się, jak używać parametrów SQL.
ms.openlocfilehash: b24610a5cb65e2b24171452acef9bf55b4995431
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/15/2020
ms.locfileid: "84768953"
---
# <a name="parameters"></a>Parametry

Parametry są używane do ochrony przed atakami polegającymi na iniekcji SQL. Zamiast łączyć dane wejściowe użytkownika z instrukcjami SQL, użyj parametrów, aby upewnić się, że dane wejściowe są kiedykolwiek traktowane jako wartość literału, a nigdy nie wykonane. W przypadku oprogramowania SQLite parametry są zwykle dozwolone wszędzie tam, gdzie literał jest dozwolony w instrukcjach SQL.

Parametry mogą być poprzedzone znakiem `:` , `@` , lub `$` .

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/HelloWorldSample/Program.cs?name=snippet_Parameter)]

Aby uzyskać szczegółowe informacje o tym, jak wartości .NET są mapowane na wartości oprogramowania SQLite, zobacz [typy danych](types.md) .

## <a name="truncation"></a>Obcięcie

Użyj <xref:Microsoft.Data.Sqlite.SqliteParameter.Size> właściwości, aby obciąć wartości tekstowe i obiekty blob.

```csharp
// Truncate name to 30 characters
command.Parameters.AddWithValue("$name", name).Size = 30;
```

## <a name="alternative-types"></a>Typy alternatywne

Czasami warto użyć alternatywnego typu oprogramowania SQLite. Aby to zrobić, należy ustawić <xref:Microsoft.Data.Sqlite.SqliteParameter.SqliteType> Właściwość.

Można użyć następujących mapowań alternatywnego typu. Aby uzyskać domyślne mapowania, zobacz [typy danych](types.md).

| Wartość          | Sqlitetype | Uwagi          |
| -------------- | ---------- | ---------------- |
| Char           | Liczba całkowita    | UTF-16           |
| DateTime       | Rzeczywiste       | Wartość w postaci ciągu juliańskim |
| DateTimeOffset | Rzeczywiste       | Wartość w postaci ciągu juliańskim |
| Guid (identyfikator GUID)           | Obiekt blob       |                  |
| przedział_czasu       | Rzeczywiste       | W dniach          |

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/DateAndTimeSample/Program.cs?name=snippet_SqliteType)]

## <a name="output-parameters"></a>Parametry wyjściowe

Produkt SQLite nie obsługuje parametrów wyjściowych. Zamiast tego Zwróć wartości w wynikach zapytania.

## <a name="see-also"></a>Zobacz też

* [Typy danych](types.md)
