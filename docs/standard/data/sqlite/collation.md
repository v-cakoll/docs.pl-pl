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

Kolejność sortowania jest używana przez program SQLite podczas porównywania wartości tekstowych, aby określić kolejność i równość. Można określić, które sortowanie ma być używane podczas tworzenia kolumn lub dla operacji na zapytania SQL. Program SQLite domyślnie zawiera trzy sekwencje sortowania.

| Sortowanie | Opis                               |
| --------- | ----------------------------------------- |
| RTRIM     | Ignoruje końcowe odstępy               |
| Nocase    | Bez uwzględniania wielkości liter dla znaków ASCII A-Z |
| BINARNY    | Wielkość liter. Porównuje bajty bezpośrednio   |

## <a name="custom-collation"></a>Sortowanie niestandardowe

Można również zdefiniować własne sekwencje sortowania lub zastąpić wbudowane przy użyciu polecenia <xref:Microsoft.Data.Sqlite.SqliteConnection.CreateCollation%2A>. W poniższym przykładzie przedstawiono przesłanianie sortowania nocase do obsługi znaków Unicode. [Pełny przykładowy kod](https://github.com/dotnet/docs/blob/master/samples/snippets/standard/data/sqlite/CollationSample/Program.cs) jest dostępny w serwisie GitHub.

[!code-csharp[](../../../../samples/snippets/standard/data/sqlite/CollationSample/Program.cs?name=snippet_Collation)]

## <a name="like-operator"></a>Like — Operator

Operator LIKE w programie SQLite nie honoruje sortowania. Domyślna implementacja ma tę samą semantykę co sortowanie nocase. W przypadku znaków ASCII od A do Z jest rozróżniana wielkość liter.

Można łatwo wprowadzić wielkość liter operatora LIKE, używając następującej instrukcji pragma:

```sql
PRAGMA case_sensitive_like = 1
```

Zobacz [funkcje zdefiniowane przez użytkownika](user-defined-functions.md) , aby uzyskać szczegółowe informacje na temat zastępowania implementacji operatora like.

## <a name="see-also"></a>Zobacz też

* [Funkcje zdefiniowane przez użytkownika](user-defined-functions.md)
* [Składnia SQL](https://www.sqlite.org/lang.html)
