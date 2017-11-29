---
title: "Obsługa wartości zerowych w wyrażeniach zapytań"
description: "Jak Obsługa wartości zerowych w wyrażeniach zapytań."
keywords: .NET, .NET core, C#
author: BillWagner
manager: wpickett
ms.author: wiwagn
ms.date: 12/1/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.assetid: ac63ae8b-724d-4251-9334-528f4e884ae7
ms.openlocfilehash: d16256e31b073a599504ffef6501ed34430a7694
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
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
