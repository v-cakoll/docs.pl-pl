---
title: Operator [] (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- '[]_CSharpKeyword'
helpviewer_keywords:
- subscript operator [C#]
- square brackets [ ] operator [C#]
- '[] operator [C#]'
- indexing operator [C#]
ms.assetid: 5c16bb45-88f7-45ff-b42c-1af1972b042c
ms.openlocfilehash: 65908bb3bcd8912ef81fc094e5958ae8dc4ae1f1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="-operator-c-reference"></a>Operator [] (odwołanie w C#)
Nawiasy kwadratowe (`[]`) są używane dla tablic, indeksatorów i atrybutów. Mogą one również używane z wskaźniki.  
  
## <a name="remarks"></a>Uwagi  
 Typ tablicy jest typem następuje `[]`:  
  
 [!code-csharp[csRefOperators#43](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_1.cs)]  
  
 Aby uzyskać dostęp do elementu tablicy, indeks żądany element jest ujęty w nawiasy:  
  
 [!code-csharp[csRefOperators#44](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_2.cs)]  
  
 Jeśli indeks tablicy jest poza zakresem, jest zgłaszany wyjątek.  
  
 Operator indeksowanie tablicy nie może zostać przeciążony; jednak typów można zdefiniować, indeksatorów i właściwości, które przyjmują co najmniej jeden parametr. Indeksator parametry są ujęte w nawiasy kwadratowe, podobnie jak indeksy tablicy, ale indeksatora parametry mogą być deklarowane jako dowolnego typu, w odróżnieniu od indeksy tablicy, które musi być wartością całkowitą.  
  
 Na przykład, .NET Framework definiuje `Hashtable` typu, który kojarzy kluczy i wartości dowolnego typu:  
  
 [!code-csharp[csRefOperators#45](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_3.cs)]  
  
 Nawiasy kwadratowe są również używane do określenia [atrybuty](../../../csharp/programming-guide/concepts/attributes/index.md):  
  
 [!code-csharp[csRefOperators#46](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_4.cs)]  
  
 Nawiasy kwadratowe umożliwia indeksu poza wskaźnik:  
  
 [!code-csharp[csRefOperators#47](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_5.cs)]  
  
 Nie granice sprawdzanie jest wykonywane.  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Operatory języka C#](../../../csharp/language-reference/operators/index.md)  
 [Tablice](../../../csharp/programming-guide/arrays/index.md)  
 [Indeksatory](../../../csharp/programming-guide/indexers/index.md)  
 [unsafe](../../../csharp/language-reference/keywords/unsafe.md)  
 [fixed, instrukcja](../../../csharp/language-reference/keywords/fixed-statement.md)
