---
title: '&amp;&amp;Operator (odwołanie w C#)'
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '&&_CSharpKeyword'
helpviewer_keywords:
- '&& operator [C#]'
- logical AND operator [C#]
ms.assetid: 2e4f0a1c-92a3-40f8-8e3b-17b607f20c31
caps.latest.revision: 18
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 16bc2fa650031d2b1f6cfaf7d128ba487963f707
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="ampamp-operator-c-reference"></a>&amp;&amp;Operator (odwołanie w C#)
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
 [Operatory C#](../../../csharp/language-reference/operators/index.md)
