---
title: '&amp;&amp; Operator (odwołanie w C#)'
ms.date: 07/20/2015
f1_keywords:
- '&&_CSharpKeyword'
helpviewer_keywords:
- '&& operator [C#]'
- logical AND operator [C#]
ms.assetid: 2e4f0a1c-92a3-40f8-8e3b-17b607f20c31
ms.openlocfilehash: 15bb3e9702f04cc805af63767c7ecbfc68160368
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2018
---
# <a name="ampamp-operator-c-reference"></a>&amp;&amp; Operator (odwołanie w C#)
Operator warunkowy i - AND, (`&&`) wykonuje koniunkcję jego argumentów typu `bool`. W razie potrzeby ocenia wartośc tylko drugiego z argumentów.  
  
## <a name="remarks"></a>Uwagi  
 Operacja  
  
```csharp  
x && y  
```  
  
 odnosi się do operacji  
  
```csharp  
x & y  
```  
  
 Z wyjątkiem tego, że jeśli `x` jest `false`, to `y` nie zostanie ocenione, ponieważ wynikiem operacji będzie `false` niezależnie od tego, jaką wartość ma `y`. Taki zabieg nazywamy oceną typu „short-circuit”.  
  
 Operator warunkowy 'AND' nie może być przeciążony, ale przeciążenia zwykłych operatorów logicznych oraz [true](../../../csharp/language-reference/keywords/true.md) i [false](../../../csharp/language-reference/keywords/false.md) są dopuszczalne z odpowiednimi ograniczeniami.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie drugi blok warunkowy `if` ocenia tylko pierwszy argumentów operacji AND, ponieważ ten zwraca wartość `false`.  
  
 [!code-csharp[csRefOperators#48](../../../csharp/language-reference/operators/codesnippet/CSharp/conditional-and-operator_1.cs)]  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Operatory języka C#](../../../csharp/language-reference/operators/index.md)
