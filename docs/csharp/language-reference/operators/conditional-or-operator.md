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
ms.openlocfilehash: 58e5fd72a3748e7af0894093fc461c4efb543608
ms.sourcegitcommit: 412bbc2e43c3b6ca25b358cdf394be97336f0c24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/25/2018
ms.locfileid: "42925543"
---
# <a name="-operator-c-reference"></a>Operator || (odwołanie w C#)
Operator warunkowy OR (`||`) wykonuje logiczne OR z jego `bool` argumentów operacji. Jeśli pierwszy operand ma wartość `true`, drugi argument nie jest poddawany ocenie. Jeśli pierwszy operand ma wartość `false`, drugi operator określa, czy wyrażenie OR jako całość daje w wyniku `true` lub `false`.  
  
## <a name="remarks"></a>Uwagi  
 Operacja  
  
```csharp  
x || y  
```  
  
 odnosi się do operacji  
  
```csharp  
x | y  
```  
  
 z wyjątkiem, że jeśli `x` jest `true`, `y` nie jest oceniany, ponieważ jest w operacji OR `true` niezależnie od wartości `y`. Takie podejście jest znana jako "ocena zwarcia".  
  
 Operator warunkowy OR nie mogą być przeciążone, ale przeciążenia regularne operatorów logicznych i [true](../../../csharp/language-reference/keywords/true.md) i [false](../../../csharp/language-reference/keywords/false.md) operatorów z pewnymi ograniczeniami również uważana za przeciążenia Operatory logiczne warunkowe.  
  
## <a name="example"></a>Przykład  
 W poniższych przykładach wyrażenia, który używa `||` oblicza tylko pierwszy operand. Wyrażenie, które używa `|` ocenia oba operandy. W drugim przykładzie wyjątek czasu wykonywania występuje, gdy oba operandy są oceniane.  
  
 [!code-csharp[csRefOperators#52](../../../csharp/language-reference/operators/codesnippet/CSharp/conditional-or-operator_1.cs)]  
  
## <a name="see-also"></a>Zobacz też

- [Dokumentacja języka C#](../../../csharp/language-reference/index.md)  
- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
- [Operatory języka C#](../../../csharp/language-reference/operators/index.md)
