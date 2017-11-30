---
title: "Operator || (odwołanie w C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: '||_CSharpKeyword'
helpviewer_keywords:
- logical OR operator [C#]
- conditional-OR operator (||) [C#]
- '|| operator [C#]'
ms.assetid: 7d442d8e-400d-421f-b4d2-034bf82bcbdc
caps.latest.revision: "25"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 7b95fd162c9a89789e1970b32473c8acf16ba5cf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a>Operator || (odwołanie w C#)
Operator warunkowy OR (`||`) wykonuje logiczne lub z jego `bool` argumentów operacji. Jeśli pierwszy argument operacji daje w wyniku `true`, drugi argument nie jest obliczane. Jeśli pierwszy argument operacji daje w wyniku `false`, drugi — operator określa, czy wyrażenie OR jako całość daje w wyniku `true` lub `false`.  
  
## <a name="remarks"></a>Uwagi  
 Operacja  
  
```  
x || y  
```  
  
 odnosi się do operacji  
  
```  
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
 [Operatory C#](../../../csharp/language-reference/operators/index.md)
