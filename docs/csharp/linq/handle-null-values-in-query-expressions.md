---
title: Obsługa wartości zerowych w wyrażeniach zapytań ( C#LINQ in)
description: Dowiedz się, jak obsłużyć wartości null w C#wyrażeniach zapytań LINQ w.
ms.date: 12/01/2016
ms.assetid: ac63ae8b-724d-4251-9334-528f4e884ae7
ms.openlocfilehash: 38a5c5e4a869cc44be78f70cbf0e50166baaab16
ms.sourcegitcommit: da2dd2772fcf32b44eb18b1cbe8affd17b1753c9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/27/2019
ms.locfileid: "71353324"
---
# <a name="handle-null-values-in-query-expressions"></a>Obsługa wartości null w wyrażeniach zapytań

Ten przykład pokazuje, jak obsługiwać możliwe wartości null w kolekcjach źródłowych. Kolekcja obiektów, taka jak <xref:System.Collections.Generic.IEnumerable%601>, może zawierać elementy, których wartość jest [równa null](../language-reference/keywords/null.md). Jeśli kolekcja źródłowa ma wartość null lub zawiera element, którego wartość jest równa null, a zapytanie nie obsługuje wartości null, podczas wykonywania zapytania zostanie wygenerowane <xref:System.NullReferenceException>.

## <a name="example"></a>Przykład

Można odpowiednio zakodować, aby uniknąć wyjątku odwołania o wartości null, jak pokazano w następującym przykładzie:

[!code-csharp[csProgGuideLINQ#82](~/samples/snippets/csharp/concepts/linq/how-to-handle-null-values-in-query-expressions_1.cs)]

W poprzednim przykładzie klauzula `where` filtruje wszystkie elementy null w sekwencji kategorii. Ta technika jest niezależna od sprawdzania wartości null w klauzuli join. Wyrażenie warunkowe mające wartość null w tym przykładzie działa, ponieważ `Products.CategoryID` jest typu `int?`, który jest skrótem dla `Nullable<int>`.

## <a name="example"></a>Przykład

W klauzuli join, jeśli tylko jeden z kluczy porównania jest typem wartości null, można rzutować inne do typu dopuszczającego wartość null w wyrażeniu zapytania. W poniższym przykładzie Załóżmy, że `EmployeeID` jest kolumną zawierającą wartości typu `int?`:

[!code-csharp[csProgGuideLINQ#83](~/samples/snippets/csharp/concepts/linq/how-to-handle-null-values-in-query-expressions_2.cs)]

## <a name="see-also"></a>Zobacz także

- <xref:System.Nullable%601>
- [Language Integrated Query (LINQ)](index.md)
- [Typy wartości null](../programming-guide/nullable-types/index.md)
