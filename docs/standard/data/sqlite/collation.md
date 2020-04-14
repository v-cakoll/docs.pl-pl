---
title: Sortowanie
ms.date: 12/13/2019
description: Dowiedz się, jak utworzyć niestandardową sekwencję sortowania.
ms.openlocfilehash: 9879846cc191a62c4cb47a0fbaa47c59153ba61c
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/13/2020
ms.locfileid: "81242975"
---
# <a name="collation"></a>Sortowanie

Sekwencje sortowania są używane przez SQLite podczas porównywania wartości TEXT w celu określenia kolejności i równości. Można określić, które sortowanie ma być używane podczas tworzenia kolumn lub operacji na operację w kwerendach SQL. SQLite zawiera domyślnie trzy sekwencje sortowania.

| Sortowanie | Opis                               |
| --------- | ----------------------------------------- |
| RTRIM     | Ignoruje końcowe odstępy               |
| NOCASE (NOCASE)    | Bez uwzględniania wielkości liter dla znaków ASCII A-Z |
| Binarnym    | Rozróżniana wielkość liter. Bezpośrednio porównuje bajty   |

## <a name="custom-collation"></a>Sortowanie niestandardowe

Można również zdefiniować własne sekwencje sortowania lub zastąpić wbudowane za pomocą programu <xref:Microsoft.Data.Sqlite.SqliteConnection.CreateCollation%2A>. Poniższy przykład przedstawia zastępowanie sortowania NOCASE do obsługi znaków Unicode. [Pełny przykładowy kod](https://github.com/dotnet/docs/blob/master/samples/snippets/standard/data/sqlite/CollationSample/Program.cs) jest dostępny w usłudze GitHub.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/CollationSample/Program.cs?name=snippet_Collation)]

## <a name="like-operator"></a>Podobnie jak operator

Operator LIKE w SQLite nie honoruje sortowania. Domyślna implementacja ma taką samą semantycę jak sortowanie NOCASE. Jest to tylko niewrażliwe na litery dla znaków ASCII od A do Z.

Można łatwo sprawić, aby przypadek operatora LIKE był rozróżniany przy użyciu następującej instrukcji pragma:

```sql
PRAGMA case_sensitive_like = 1
```

Zobacz [funkcje zdefiniowane przez użytkownika,](user-defined-functions.md) aby uzyskać szczegółowe informacje na temat zastępowania implementacji operatora LIKE.

## <a name="see-also"></a>Zobacz też

* [Funkcje zdefiniowane przez użytkownika](user-defined-functions.md)
* [Składnia SQL](https://www.sqlite.org/lang.html)
