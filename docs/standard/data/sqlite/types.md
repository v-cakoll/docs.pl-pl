---
title: Typy danych
ms.date: 12/13/2019
description: Opisuje obsługiwane typy danych i niektóre z tych ograniczeń.
ms.openlocfilehash: ae70cb91a5a6d9cfed45a5a47dda25a70362871e
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447182"
---
# <a name="data-types"></a>Typy danych

Program SQLite ma tylko cztery pierwotne typy danych: INTEGER, REAL, TEXT i BLOB. Interfejsy API, które zwracają wartości bazy danych jako `object`, będą kiedykolwiek zwracały jeden z tych czterech typów. Dodatkowe typy .NET są obsługiwane przez firmę Microsoft. Data. SQLite, ale wartości są ostatecznie przekształcane między tymi typami a jednym z czterech typów pierwotnych.

| .NET           | SQLite  | Uwagi                                                       |
| -------------- | ------- | ------------------------------------------------------------- |
| Boolean        | INTEGER | `0` lub `1`                                                    |
| Byte           | INTEGER |                                                               |
| Byte[]         | BLOB    |                                                               |
| Char           | TEXT    | UTF-8                                                         |
| DataGodzina       | TEXT    | RRRR-MM-DD HH: mm: SS. FFFFFFF                                   |
| DateTimeOffset | TEXT    | RRRR-MM-DD HH: mm: SS. FFFFFFFzzz                                |
| Wartość dziesiętna        | TEXT    | `0.0###########################` format. RZECZYWISTE byłyby stratne. |
| Double         | REAL    |                                                               |
| Guid           | TEXT    | 00000000-0000-0000-0000-000000000000                          |
| Int16          | INTEGER |                                                               |
| Int32          | INTEGER |                                                               |
| Int64          | INTEGER |                                                               |
| SByte          | INTEGER |                                                               |
| Single         | REAL    |                                                               |
| String         | TEXT    | UTF-8                                                         |
| przedział_czasu       | TEXT    | d. hh: mm: SS. fffffff                                            |
| UInt16         | INTEGER |                                                               |
| UInt64         | INTEGER | Przepełnienie dużych wartości                                         |

## <a name="alternative-types"></a>Typy alternatywne

Niektóre typy .NET można odczytać z alternatywnych typów oprogramowania SQLite. Parametry można także skonfigurować tak, aby korzystały z tych alternatywnych typów. Aby uzyskać więcej informacji, zobacz [Parametry](parameters.md#alternative-types).

| .NET           | SQLite  | Uwagi          |
| -------------- | ------- | ---------------- |
| Char           | INTEGER | UTF-16           |
| DataGodzina       | REAL    | Wartość w postaci ciągu juliańskim |
| DateTimeOffset | REAL    | Wartość w postaci ciągu juliańskim |
| Guid           | BLOB    |                  |
| przedział_czasu       | REAL    | W dniach          |

Na przykład następujące zapytanie odczytuje wartość TimeSpan z RZECZYWISTEj kolumny w zestawie wyników.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/DateAndTimeSample/Program.cs?name=snippet_AlternativeType)]

## <a name="column-types"></a>Typy kolumn

Program SQLite używa systemu typu dynamicznego, w którym typ wartości jest skojarzony z samą wartością, a nie z kolumną, w której jest przechowywana. Możesz użyć dowolnej nazwy typu kolumny. Microsoft. Data. sqlite nie zastosuje żadnej dodatkowej semantyki do tych nazw.

Nazwa typu kolumny ma wpływ na [koligację typu](https://www.sqlite.org/datatype3.html#type_affinity). Jednym z typowych Gotcha jest użycie typu kolumny STRING, próba konwersji wartości na liczbę całkowitą lub RZECZYWISTą, co może prowadzić do nieoczekiwanych wyników. Zalecamy używanie tylko czterech pierwotnych nazw typów oprogramowania SQLite: INTEGER, REAL, TEXT i BLOB.

Program SQLite pozwala określić aspekty typu, takie jak długość, precyzja i skala, ale nie są wymuszane przez aparat bazy danych. Aplikacja jest odpowiedzialna za wymuszanie tych.

## <a name="see-also"></a>Zobacz także

- [Typy danych w programie SQLite](https://www.sqlite.org/datatype3.html)
