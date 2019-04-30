---
title: Obsługa wartości zerowych w wyrażeniach zapytań (LINQ w C#)
description: Dowiedz się, jak Obsługa wartości zerowych w wyrażeniach zapytań LINQ w C#.
ms.date: 12/01/2016
ms.assetid: ac63ae8b-724d-4251-9334-528f4e884ae7
ms.openlocfilehash: 14609aee2bbd1fbb487589bb41683a1f3cad1362
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61659894"
---
# <a name="handle-null-values-in-query-expressions"></a>Obsługa wartości null w wyrażeniach zapytań

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
