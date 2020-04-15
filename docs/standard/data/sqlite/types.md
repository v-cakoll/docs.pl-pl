---
title: Typy danych
ms.date: 12/13/2019
description: W tym artykule opisano obsługiwane typy danych i niektóre ograniczenia wokół nich.
ms.openlocfilehash: a11ff382f80cd979506d6195c299c8234c3eb8ea
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389044"
---
# <a name="data-types"></a>Typy danych

SQLite ma tylko cztery podstawowe typy danych: INTEGER, REAL, TEXT i BLOB. Interfejsy API, które zwracają `object` wartości bazy danych jako będzie zwracać tylko jeden z tych czterech typów. Dodatkowe typy .NET są obsługiwane przez microsoft.Data.Sqlite, ale wartości są ostatecznie wymuszane między tymi typami i jednym z czterech typów pierwotnych.

| .NET           | SQLite  | Uwagi                                                       |
| -------------- | ------- | ------------------------------------------------------------- |
| Wartość logiczna        | LICZBA CAŁKOWITA | `0` lub `1`                                                    |
| Byte           | LICZBA CAŁKOWITA |                                                               |
| Bajt[]         | Blob    |                                                               |
| Char           | TEKST    | UTF-8                                                         |
| DateTime       | TEKST    | yyyy-MM-dd HH:mm:ss. Fffffff                                   |
| Datetimeoffset | TEKST    | yyyy-MM-dd HH:mm:ss. FFFFFzzz                                |
| Wartość dziesiętna        | TEKST    | `0.0###########################`Formacie. REAL byłby stratny. |
| Double         | LICZBA RZECZYWISTA    |                                                               |
| Guid (identyfikator GUID)           | TEKST    | 00000000-0000-0000-0000-000000000000                          |
| Int16          | LICZBA CAŁKOWITA |                                                               |
| Int32          | LICZBA CAŁKOWITA |                                                               |
| Int64          | LICZBA CAŁKOWITA |                                                               |
| SByte          | LICZBA CAŁKOWITA |                                                               |
| Single         | LICZBA RZECZYWISTA    |                                                               |
| Ciąg         | TEKST    | UTF-8                                                         |
| przedział_czasu       | TEKST    | d.hh:mm:ss.fffffff                                            |
| UInt16         | LICZBA CAŁKOWITA |                                                               |
| UInt32         | LICZBA CAŁKOWITA |                                                               |
| UInt64         | LICZBA CAŁKOWITA | Przepełnienie dużych wartości                                         |

## <a name="alternative-types"></a>Typy alternatywne

Niektóre typy .NET można odczytać z alternatywnych typów SQLite. Parametry można również skonfigurować do używania tych typów alternatywnych. Aby uzyskać więcej informacji, zobacz [Parametry](parameters.md#alternative-types).

| .NET           | SQLite  | Uwagi          |
| -------------- | ------- | ---------------- |
| Char           | LICZBA CAŁKOWITA | UTF-16           |
| DateTime       | LICZBA RZECZYWISTA    | Wartość dnia juliańskiego |
| Datetimeoffset | LICZBA RZECZYWISTA    | Wartość dnia juliańskiego |
| Guid (identyfikator GUID)           | Blob    |                  |
| przedział_czasu       | LICZBA RZECZYWISTA    | W dniach          |

Na przykład następująca kwerenda odczytuje timespan wartość z kolumny REAL w zestawie wyników.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/DateAndTimeSample/Program.cs?name=snippet_AlternativeType)]

## <a name="column-types"></a>Typy kolumn

SQLite używa systemu typów dynamicznych, w którym typ wartości jest skojarzony z samą wartością, a nie z kolumną, w której jest przechowywana. Możesz używać dowolnej nazwy typu kolumny. Microsoft.Data.Sqlite nie zastosuje żadnych dodatkowych semantyki do tych nazw.

Nazwa typu kolumny ma wpływ na [koligacji typu](https://www.sqlite.org/datatype3.html#type_affinity). Jednym z typowych gotcha jest to, że przy użyciu typu kolumny STRING spróbuje przekonwertować wartości do INTEGER lub REAL, co może prowadzić do nieoczekiwanych wyników. Firma Microsoft zaleca tylko przy użyciu czterech pierwotnych nazw typów SQLite: INTEGER, REAL, TEXT i BLOB.

SQLite umożliwia określenie aspektów typu, takich jak długość, precyzja i skala, ale nie są one wymuszane przez aparat bazy danych. Aplikacja jest odpowiedzialna za ich egzekwowanie.

## <a name="see-also"></a>Zobacz też

- [Typy danych w sqlite](https://www.sqlite.org/datatype3.html)
