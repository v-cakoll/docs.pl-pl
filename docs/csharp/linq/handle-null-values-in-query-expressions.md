---
title: Obsługa wartości null w wyrażeniach kwerendy (LINQ w języku C#)
description: Dowiedz się, jak obsługiwać wartości null w wyrażeniach kwerend LINQ w języku C#.
ms.date: 12/01/2016
ms.assetid: ac63ae8b-724d-4251-9334-528f4e884ae7
ms.openlocfilehash: c9a3aaec05fa029a8db66826bdcb4a1d106176e3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "73736855"
---
# <a name="handle-null-values-in-query-expressions"></a>Obsługa wartości null w wyrażeniach zapytań

W tym przykładzie pokazano, jak obsługiwać możliwe wartości null w kolekcjach źródłowych. Kolekcja obiektów, takich <xref:System.Collections.Generic.IEnumerable%601> jak może zawierać elementy, których wartość jest [null](../language-reference/keywords/null.md). Jeśli kolekcja źródłowa ma wartość null lub zawiera element, którego wartość <xref:System.NullReferenceException> ma wartość null, a kwerenda nie obsługuje wartości null, podczas wykonywania kwerendy zostanie wygenerowany.

## <a name="example"></a>Przykład

Można kod defensywnie, aby uniknąć wyjątku odwołania zerowego, jak pokazano w poniższym przykładzie:

[!code-csharp[csProgGuideLINQ#82](~/samples/snippets/csharp/concepts/linq/how-to-handle-null-values-in-query-expressions_1.cs)]

W poprzednim przykładzie `where` klauzula odfiltrowuje wszystkie elementy null w sekwencji kategorii. Ta technika jest niezależna od sprawdzania wartości null w klauzuli join. Wyrażenie warunkowe z null w `Products.CategoryID` tym przykładzie `int?` działa, ponieważ `Nullable<int>`jest typu, który jest skrótem dla .

## <a name="example"></a>Przykład

W join klauzuli, jeśli tylko jeden z kluczy porównania jest typem wartości nullable, można rzutować drugi do typu nullable w wyrażeniu kwerendy. W poniższym przykładzie `EmployeeID` załóżmy, że jest `int?`to kolumna zawierająca wartości typu:

[!code-csharp[csProgGuideLINQ#83](~/samples/snippets/csharp/concepts/linq/how-to-handle-null-values-in-query-expressions_2.cs)]

## <a name="see-also"></a>Zobacz też

- <xref:System.Nullable%601>
- [Language Integrated Query (LINQ)](index.md)
- [Typy wartości z możliwością null](../language-reference/builtin-types/nullable-value-types.md)
