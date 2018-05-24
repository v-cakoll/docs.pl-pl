---
title: () — Operator (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- ()_CSharpKeyword
helpviewer_keywords:
- type conversion [C#], () operator
- cast operator [C#]
- () operator [C#]
ms.assetid: 846e1f94-8a8c-42fc-a42c-fbd38e70d8cc
ms.openlocfilehash: 2ded01ef3192e0f34d586cd63d93b894b5347e7e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="-operator-c-reference"></a>() — Operator (odwołanie w C#)
Oprócz określania kolejności operacji w wyrażeniach nawiasy są też używane do następujących zadań: 
  
1. Określanie rzutowania lub konwersji typów.
  
     [!code-csharp[csRefOperators#1](../../../csharp/language-reference/operators/codesnippet/CSharp/invocation-operator_1.cs)]  
  
2. Wywołanie metod lub obiektów delegowanych.
  
     [!code-csharp[csRefOperators#2](../../../csharp/language-reference/operators/codesnippet/CSharp/invocation-operator_2.cs)]  
  
## <a name="remarks"></a>Uwagi  
 Rzutowanie jawnie wywołuje operatora konwersji z jednego typu do drugiego. Rzutowanie kończy się niepowodzeniem, jeśli żaden operator konwersji nie jest zdefiniowany. Aby zdefiniować operatora konwersji, zobacz [jawne](../../../csharp/language-reference/keywords/explicit.md) i [niejawne](../../../csharp/language-reference/keywords/implicit.md) definiowanie operatorów konwersji.
  
 Operator `()` nie może być przeciążony.  
  
 Aby uzyskać więcej informacji, zobacz [rzutowanie i konwersje typów](../../../csharp/programming-guide/types/casting-and-type-conversions.md).  
  
 Wyrażenie cast może prowadzić do niejednoznaczności składni. Na przykład wyrażenie `(x)–y` może być interpretowane jako wyrażenie cast (rzutowanie -y na typ x) lub jako wyrażenie addytywne połączone z wyrażeniem w nawiasie, które oblicza wartość x — y.
  
 Aby uzyskać więcej informacji na temat wywołania metody, zobacz [metody](../../../csharp/programming-guide/classes-and-structs/methods.md).  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  

 [Operatory języka C#](../../../csharp/language-reference/operators/index.md)