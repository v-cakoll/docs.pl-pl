---
title: Obsługa wartości zerowych w wyrażeniach zapytań (LINQ w C#)
description: Dowiedz się, jak Obsługa wartości zerowych w wyrażeniach zapytań LINQ w C#.
ms.date: 12/1/2016
ms.assetid: ac63ae8b-724d-4251-9334-528f4e884ae7
ms.openlocfilehash: 2c477ef371dbb424c72fb9d34948760b7e3f5609
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43797760"
---
# <a name="handle-null-values-in-query-expressions"></a>Obsługa wartości zerowych w wyrażeniach zapytań

Ten przykład przedstawia sposób obsługi możliwych wartości null w kolekcji źródłowej. Kolekcja obiektów, takich jak <xref:System.Collections.Generic.IEnumerable%601> może zawierać elementy, których wartość jest [null](../language-reference/keywords/null.md). Jeśli kolekcja źródłowa jest pusta lub zawiera element, którego wartość jest równa null, a zapytanie nie obsługuje wartości null, <xref:System.NullReferenceException> zostanie zgłoszony podczas wykonywania zapytania.

## <a name="example"></a>Przykład

Możesz tworzyć kod pamiętać o uniknąć wyjątek pustej referencji, jak pokazano w poniższym przykładzie:

[!code-csharp[csProgGuideLINQ#82](~/samples/snippets/csharp/concepts/linq/how-to-handle-null-values-in-query-expressions_1.cs)]

W poprzednim przykładzie `where` klauzuli odfiltrowuje wszystkie elementy o wartości null w sekwencji kategorii. Ta technika jest niezależny od sprawdzanie wartości null w klauzuli join. Wyrażenie warunkowe z wartością null, w tym przykładzie działa, ponieważ `Products.CategoryID` typu `int?` co jest skrótem `Nullable<int>`.

## <a name="example"></a>Przykład

W klauzuli join jeśli tylko jeden z kluczy porównania jest typem wartościowym, można rzutować z drugiej strony do typu dopuszczającego wartość null w wyrażeniu zapytania. W poniższym przykładzie przyjęto założenie, że `EmployeeID` to kolumna, która zawiera wartości typu `int?`:

[!code-csharp[csProgGuideLINQ#83](~/samples/snippets/csharp/concepts/linq/how-to-handle-null-values-in-query-expressions_2.cs)]

## <a name="see-also"></a>Zobacz także

- <xref:System.Nullable%601>  
- [Language Integrated Query (LINQ)](index.md)  
- [Typy dopuszczające wartości zerowe](../programming-guide/nullable-types/index.md)  
