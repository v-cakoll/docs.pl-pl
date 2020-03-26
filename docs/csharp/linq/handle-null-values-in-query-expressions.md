---
title: Obsługa wartości null w wyrażeniach kwerendy (LINQ w języku C#)
description: Dowiedz się, jak obsługiwać wartości null w wyrażeniach zapytania LINQ w języku C#.
ms.date: 12/01/2016
ms.assetid: ac63ae8b-724d-4251-9334-528f4e884ae7
ms.openlocfilehash: 3da490b72bd518df7be8c14b34655af8c6f84929
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2020
ms.locfileid: "80249308"
---
# <a name="handle-null-values-in-query-expressions"></a>Obsługa wartości null w wyrażeniach zapytań

W tym przykładzie pokazano, jak obsługiwać możliwe wartości null w kolekcjach źródłowych. Kolekcja obiektów, taka <xref:System.Collections.Generic.IEnumerable%601> jak może zawierać elementy, których wartość jest [null](../language-reference/keywords/null.md). Jeśli kolekcja źródło ma wartość null lub zawiera element, którego wartość jest <xref:System.NullReferenceException> null, a kwerenda nie obsługuje wartości null, zostanie ono odrzucone podczas wykonywania kwerendy.

## <a name="example"></a>Przykład

Można kodować defensywnie, aby uniknąć wyjątku odwołania null, jak pokazano w poniższym przykładzie:

[!code-csharp[csProgGuideLINQ#82](~/samples/snippets/csharp/concepts/linq/how-to-handle-null-values-in-query-expressions_1.cs)]

W poprzednim przykładzie `where` klauzula odfiltruje wszystkie elementy null w sekwencji kategorii. Ta technika jest niezależna od sprawdzania wartości null w klauzuli sprzężenia. Wyrażenie warunkowe z null w `Products.CategoryID` tym przykładzie działa, ponieważ jest typu, `int?` który jest skrótem dla `Nullable<int>`.

## <a name="example"></a>Przykład

W klauzuli sprzężenia, jeśli tylko jeden z kluczy porównania jest typem wartości możliwej do wartości null, można rzutować drugą do typu wartości możliwej do wartości null w wyrażeniu kwerendy. W poniższym przykładzie `EmployeeID` załóżmy, że `int?`jest to kolumna zawierająca wartości typu:

[!code-csharp[csProgGuideLINQ#83](~/samples/snippets/csharp/concepts/linq/how-to-handle-null-values-in-query-expressions_2.cs)]

## <a name="see-also"></a>Zobacz też

- <xref:System.Nullable%601>
- [Language Integrated Query (LINQ)](index.md)
- [Typy wartości możliwe do wartości null](../language-reference/builtin-types/nullable-value-types.md)
