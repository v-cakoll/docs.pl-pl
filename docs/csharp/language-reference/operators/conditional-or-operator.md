---
title: Operator || (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- '||_CSharpKeyword'
helpviewer_keywords:
- logical OR operator [C#]
- conditional-OR operator (||) [C#]
- '|| operator [C#]'
ms.assetid: 7d442d8e-400d-421f-b4d2-034bf82bcbdc
ms.openlocfilehash: d22e57d097edb0fe52b604e9c6431e167c410f0b
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2018
---
# <a name="-operator-c-reference"></a>Operator || (odwołanie w C#)
Operator warunkowy OR (`||`) wykonuje logiczne lub z jego `bool` argumentów operacji. Jeśli pierwszy argument operacji daje w wyniku `true`, drugi argument nie jest obliczane. Jeśli pierwszy argument operacji daje w wyniku `false`, drugi — operator określa, czy wyrażenie OR jako całość daje w wyniku `true` lub `false`.  
  
## <a name="remarks"></a>Uwagi  
 Operacja  
  
```csharp  
x || y  
```  
  
 odnosi się do operacji  
  
```csharp  
x | y  
```  
  
 z wyjątkiem, że jeśli `x` jest `true`, `y` nie jest oceniany, ponieważ operacja OR `true` niezależnie od wartości `y`. To pojęcie jest ogólnie znana jako "zwarcia" oceny.  
  
 Operator warunkowy OR nie może zostać przeciążony, ale overloads regularnych operatorów logicznych i [true](../../../csharp/language-reference/keywords/true.md) i [false](../../../csharp/language-reference/keywords/false.md) operatorów z pewnymi ograniczeniami również uważa się za przeciążenia Operatory logiczne warunkowe.  
  
## <a name="example"></a>Przykład  
 W poniższych przykładach wyrażenia, który używa `||` ocenia tylko pierwszy argument operacji. Wyrażenie, które używa `|` ocenia oba argumenty. W drugim przykładzie wyjątek czasu wykonywania występuje, jeśli obydwa argumenty operacji są oceniane.  
  
 [!code-csharp[csRefOperators#52](../../../csharp/language-reference/operators/codesnippet/CSharp/conditional-or-operator_1.cs)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Operatory języka C#](../../../csharp/language-reference/operators/index.md)
