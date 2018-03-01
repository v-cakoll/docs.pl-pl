---
title: "() — Operator (odwołanie w C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- ()_CSharpKeyword
helpviewer_keywords:
- type conversion [C#], () operator
- cast operator [C#]
- () operator [C#]
ms.assetid: 846e1f94-8a8c-42fc-a42c-fbd38e70d8cc
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 6d62e6c93dcc69c892d4ca96ace3806cb1c8d989
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a>() — Operator (odwołanie w C#)
Oprócz używane, aby określić kolejność operacji w wyrażeniu, nawiasy są używane do wykonywania następujących zadań:  
  
1.  Określ rzutowania lub konwersje typów.  
  
     [!code-csharp[csRefOperators#1](../../../csharp/language-reference/operators/codesnippet/CSharp/invocation-operator_1.cs)]  
  
2.  Wywołanie metod lub obiektów delegowanych.  
  
     [!code-csharp[csRefOperators#2](../../../csharp/language-reference/operators/codesnippet/CSharp/invocation-operator_2.cs)]  
  
## <a name="remarks"></a>Uwagi  
 Rzutowanie jawnie wywołuje operatora konwersji z jednego typu Rzutowanie kończy się niepowodzeniem, jeśli żaden operator konwersji jest zdefiniowany. Aby zdefiniować operator konwersji, zobacz [jawne](../../../csharp/language-reference/keywords/explicit.md) i [niejawne](../../../csharp/language-reference/keywords/implicit.md).  
  
 `()` Operator nie może być przeciążony.  
  
 Aby uzyskać więcej informacji, zobacz [rzutowanie i konwersje typów](../../../csharp/programming-guide/types/casting-and-type-conversions.md).  
  
 Wyrażenie cast może prowadzić do składni niejednoznaczne. Na przykład, wyrażenie `(x)–y` może być albo interpretowane jako wyrażenie cast (rzutowania y — typ x) lub jako dodatek wyrażenie w połączeniu z wyrażenia ujętego w nawiasy, który oblicza wartość x — y.  
  
 Aby uzyskać więcej informacji na temat wywołania metody, zobacz [metody](../../../csharp/programming-guide/classes-and-structs/methods.md).  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Operatory C#](../../../csharp/language-reference/operators/index.md)
