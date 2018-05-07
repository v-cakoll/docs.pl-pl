---
title: Operator [] (odwołanie w C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '[]_CSharpKeyword'
helpviewer_keywords:
- subscript operator [C#]
- square brackets [ ] operator [C#]
- '[] operator [C#]'
- indexing operator [C#]
ms.assetid: 5c16bb45-88f7-45ff-b42c-1af1972b042c
caps.latest.revision: 20
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 03664f5604bb7d7dce9e8ae2ff0ec045c6a203b1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a>Operator [] (odwołanie w C#)
Nawiasy kwadratowe (`[]`) są używane do obsługi tablic, indeksatorów i atrybutów. Mogą być również używane ze wskaźnikami.  
  
## <a name="remarks"></a>Uwagi  
 Typ tablicy jest typem następującym po `[]`:  
  
 [!code-csharp[csRefOperators#43](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_1.cs)]  
  
 Aby uzyskać dostęp do elementu tablicy, indeks żądanego elementu musi zostać ujęty w nawiasy kwadratowe:  
  
 [!code-csharp[csRefOperators#44](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_2.cs)]  
  
 Jeśli indeks tablicy jest poza zakresem, jest zgłaszany wyjątek. 
  
 Operator indeksowania tablicy nie może zostać przeciążony. Jednak typy mogą definiować indeksatory oraz właściwości, które przyjmują jeden lub więcej parametrów. Parametry indeksatora są ujęte w nawiasy kwadratowe, podobnie jak indeksy tablicy, ale parametry indeksatora mogą być deklarowane jako dowolny typ — w odróżnieniu od indeksów tablicy, które muszą być wartością całkowitą.   
  
 Na przykład: .NET Framework definiuje typ `Hashtable`, który kojarzy klucze i wartości dowolnego typu: 
  
 [!code-csharp[csRefOperators#45](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_3.cs)]  
  
 Nawiasy kwadratowe są również używane do określenia [atrybutów](../../../csharp/programming-guide/concepts/attributes/index.md):  
  
 [!code-csharp[csRefOperators#46](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_4.cs)]  
  
 Nawiasów kwadratowych można użyć do odindeksowania wskaźnika:
  
 [!code-csharp[csRefOperators#47](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_5.cs)]  
  
 Nie jest wykonywane sprawdzanie granic.  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Operatory C#](../../../csharp/language-reference/operators/index.md)  
 [Tablice](../../../csharp/programming-guide/arrays/index.md)  
 [Indeksatory](../../../csharp/programming-guide/indexers/index.md)  
 [unsafe](../../../csharp/language-reference/keywords/unsafe.md)  
 [Fixed — instrukcja](../../../csharp/language-reference/keywords/fixed-statement.md)
