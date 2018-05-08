---
title: '&amp;&amp; Operator (odwołanie w C#)'
ms.date: 07/20/2015
f1_keywords:
- '&&_CSharpKeyword'
helpviewer_keywords:
- '&& operator [C#]'
- logical AND operator [C#]
ms.assetid: 2e4f0a1c-92a3-40f8-8e3b-17b607f20c31
ms.openlocfilehash: 86508c6eeb2998c6f202608f9204b72b60786e4a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="ampamp-operator-c-reference"></a>&amp;&amp; Operator (odwołanie w C#)
Warunkowe — i — operator (`&&`) wykonuje logiczną — i jego `bool` argumentów operacji, ale tylko ocenia jego drugiego operandu w razie potrzeby.  
  
## <a name="remarks"></a>Uwagi  
 Operacja  
  
```  
x && y  
```  
  
 odnosi się do operacji  
  
```  
x & y  
```  
  
 z wyjątkiem, że jeśli `x` jest `false`, `y` nie jest oceniany, ponieważ wynik operacji i `false` niezależnie od tego, jakie wartości `y` jest. Jest to określane jako "zwarcia" oceny.  
  
 Warunkowe- i operator nie może być przeciążona, overloads regularnych operatorów logicznych, ale i operatory [true](../../../csharp/language-reference/keywords/true.md) i [false](../../../csharp/language-reference/keywords/false.md) z pewnymi ograniczeniami również pełnią funkcję przeciążenia Operatory logiczne warunkowego.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie wyrażenia warunkowego, w ciągu sekundy `if` instrukcji ocenia tylko pierwszy argument operacji, ponieważ argument zwraca `false`.  
  
 [!code-csharp[csRefOperators#48](../../../csharp/language-reference/operators/codesnippet/CSharp/conditional-and-operator_1.cs)]  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Operatory języka C#](../../../csharp/language-reference/operators/index.md)
