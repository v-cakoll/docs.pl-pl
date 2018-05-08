---
title: Obsługa wartości zerowych w wyrażeniach zapytań
description: Jak Obsługa wartości zerowych w wyrażeniach zapytań.
ms.date: 12/1/2016
ms.assetid: ac63ae8b-724d-4251-9334-528f4e884ae7
ms.openlocfilehash: ecd174462ef51a6dd7b7696abb9e111fc32d9ec7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="handle-null-values-in-query-expressions"></a>Obsługa wartości zerowych w wyrażeniach zapytań

Ten przykład przedstawia sposób obsługi możliwych wartości null w kolekcji źródłowej. Kolekcji obiektów, takich jak <xref:System.Collections.Generic.IEnumerable%601> może zawierać elementy o wartości [null](../language-reference/keywords/null.md). Jeśli kolekcja źródłowa ma wartość null lub zawiera element, którego wartość jest równa null, a zapytanie nie obsługuje wartości null, <xref:System.NullReferenceException> zostanie zgłoszony podczas wykonywania zapytania.  
  
## <a name="example"></a>Przykład

 Można pamiętać o kodu w celu uniknięcia wyjątek odwołania zerowego, jak pokazano w poniższym przykładzie:  
  
 [!code-csharp[csProgGuideLINQ#82](../../../samples/snippets/csharp/concepts/linq/how-to-handle-null-values-in-query-expressions_1.cs)]  
  
 W poprzednim przykładzie `where` klauzuli odfiltrowuje wszystkie elementy null w sekwencji kategorii. Ta technika jest niezależna od sprawdzania wartości null w klauzuli join. Wyrażenie warunkowe przy użyciu wartości null w tym przykładzie działa, ponieważ `Products.CategoryID` jest typu `int?` który jest skróconą formą `Nullable<int>`.  
  
## <a name="example"></a>Przykład

 W klauzuli join jeśli tylko jeden z kluczy porównania jest typem wartości NULL można rzutować drugą do typu dopuszczającego wartość null w wyrażeniu zapytania. W poniższym przykładzie przyjęto założenie, że `EmployeeID` jest kolumna zawierająca wartości typu `int?`:  
  
 [!code-csharp[csProgGuideLINQ#83](../../../samples/snippets/csharp/concepts/linq/how-to-handle-null-values-in-query-expressions_2.cs)]  
  
## <a name="see-also"></a>Zobacz także  
 <xref:System.Nullable%601>  
 [Wyrażenia zapytań LINQ](index.md)  
 [Typy dopuszczające wartości zerowe](../programming-guide/nullable-types/index.md)
