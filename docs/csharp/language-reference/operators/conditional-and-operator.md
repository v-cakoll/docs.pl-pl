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
Operator warunkowy i - AND, (`&&`) wykonuje koniunkcję jego argumentów typu `bool`. W razie potrzeby ocenia wartośc tylko drugiego z argumentów.  
  
## <a name="remarks"></a>Uwagi  
 Operacja  
  
```  
x && y  
```  
  
 Odpowiada operacji  
  
```  
x & y  
```  
  
 Za wyjątkiem tego, że jeśli `x` jest `false`, to `y` nie zostanie ocenione, ponieważ wynikiem operacji będzie `false` niezależnie od tego, jakiej wartości jest `y`. Taki zabieg nazywamy 'skrótem logicznym'.  
  
 Operator warunkowy 'AND' nie może być przeciążony, ale przeciążenia zwykłych operatorów logicznych, oraz [true](../../../csharp/language-reference/keywords/true.md) i [false](../../../csharp/language-reference/keywords/false.md) są dopuszczalne z odpowiednimi ograniczeniami.
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie, drugi blok warunkowy `if` ocenia tylko pierwszy z argumentów operatora `AND`, ponieważ ten zwraca `false`.  
  
 [!code-csharp[csRefOperators#48](../../../csharp/language-reference/operators/codesnippet/CSharp/conditional-and-operator_1.cs)]  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Operatory C#](../../../csharp/language-reference/operators/index.md)
