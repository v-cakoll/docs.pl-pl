---
title: Typy danych
ms.date: 12/13/2019
description: Opisuje obsługiwane typy danych i niektóre z tych ograniczeń.
ms.openlocfilehash: a11ff382f80cd979506d6195c299c8234c3eb8ea
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389044"
---
# <a name="data-types"></a>Typy danych

Program SQLite ma tylko cztery pierwotne typy danych: INTEGER, REAL, TEXT i BLOB. Interfejsy API, które zwracają wartości bazy `object` danych jako, będą kiedykolwiek zwracały jeden z tych czterech typów. Dodatkowe typy .NET są obsługiwane przez firmę Microsoft. Data. SQLite, ale wartości są ostatecznie przekształcane między tymi typami a jednym z czterech typów pierwotnych.

| .NET           | SQLite  | Uwagi                                                       |
| -------------- | ------- | ------------------------------------------------------------- |
| Wartość logiczna        | LICZBA CAŁKOWITA | `0` lub `1`                                                    |
| Byte           | LICZBA CAŁKOWITA |                                                               |
| Byte []         | TWORZENIA    |                                                               |
| Char           | TEKST    | UTF-8                                                         |
| DateTime       | TEKST    | RRRR-MM-DD HH: mm: SS. FFFFFFF                                   |
| DateTimeOffset | TEKST    | RRRR-MM-DD HH: mm: SS. FFFFFFFzzz                                |
| Wartość dziesiętna        | TEKST    | `0.0###########################`Formatowanie. RZECZYWISTE byłyby stratne. |
| Double         | LICZBA RZECZYWISTA    |                                                               |
| Guid (identyfikator GUID)           | TEKST    | 00000000-0000-0000-0000-000000000000                          |
| Int16          | LICZBA CAŁKOWITA |                                                               |
| Int32          | LICZBA CAŁKOWITA |                                                               |
| Int64          | LICZBA CAŁKOWITA |                                                               |
| SByte          | LICZBA CAŁKOWITA |                                                               |
| Single         | LICZBA RZECZYWISTA    |                                                               |
| Ciąg         | TEKST    | UTF-8                                                         |
| przedział_czasu       | TEKST    | d. hh: mm: SS. fffffff                                            |
| UInt16         | LICZBA CAŁKOWITA |                                                               |
| UInt32         | LICZBA CAŁKOWITA |                                                               |
| UInt64         | LICZBA CAŁKOWITA | Przepełnienie dużych wartości                                         |

## <a name="alternative-types"></a>Typy alternatywne

Niektóre typy .NET można odczytać z alternatywnych typów oprogramowania SQLite. Parametry można także skonfigurować tak, aby korzystały z tych alternatywnych typów. Aby uzyskać więcej informacji, zobacz [Parametry](parameters.md#alternative-types).

| .NET           | SQLite  | Uwagi          |
| -------------- | ------- | ---------------- |
| Char           | LICZBA CAŁKOWITA | UTF-16           |
| DateTime       | LICZBA RZECZYWISTA    | Wartość w postaci ciągu juliańskim |
| DateTimeOffset | LICZBA RZECZYWISTA    | Wartość w postaci ciągu juliańskim |
| Guid (identyfikator GUID)           | TWORZENIA    |                  |
| przedział_czasu       | LICZBA RZECZYWISTA    | W dniach          |

Na przykład następujące zapytanie odczytuje wartość TimeSpan z RZECZYWISTEj kolumny w zestawie wyników.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/DateAndTimeSample/Program.cs?name=snippet_AlternativeType)]

## <a name="column-types"></a>Typy kolumn

Program SQLite używa systemu typu dynamicznego, w którym typ wartości jest skojarzony z samą wartością, a nie z kolumną, w której jest przechowywana. Możesz użyć dowolnej nazwy typu kolumny. Microsoft. Data. sqlite nie zastosuje żadnej dodatkowej semantyki do tych nazw.

Nazwa typu kolumny ma wpływ na [koligację typu](https://www.sqlite.org/datatype3.html#type_affinity). Jednym z typowych Gotcha jest użycie typu kolumny STRING, próba konwersji wartości na liczbę całkowitą lub RZECZYWISTą, co może prowadzić do nieoczekiwanych wyników. Zalecamy używanie tylko czterech pierwotnych nazw typów oprogramowania SQLite: INTEGER, REAL, TEXT i BLOB.

Program SQLite pozwala określić aspekty typu, takie jak długość, precyzja i skala, ale nie są wymuszane przez aparat bazy danych. Aplikacja jest odpowiedzialna za wymuszanie tych.

## <a name="see-also"></a>Zobacz też

- [Typy danych w programie SQLite](https://www.sqlite.org/datatype3.html)
