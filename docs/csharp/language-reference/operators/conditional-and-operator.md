---
title: '&amp;&amp; Operator (odwołanie w C#)'
ms.date: 07/20/2015
f1_keywords:
- '&&_CSharpKeyword'
helpviewer_keywords:
- '&& operator [C#]'
- logical AND operator [C#]
ms.assetid: 2e4f0a1c-92a3-40f8-8e3b-17b607f20c31
ms.openlocfilehash: 459b791fde3e4d3940dbd3d916f940e81f365da6
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43388296"
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

- [Dokumentacja języka C#](../../../csharp/language-reference/index.md)  
- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
- [Operatory języka C#](../../../csharp/language-reference/operators/index.md)
