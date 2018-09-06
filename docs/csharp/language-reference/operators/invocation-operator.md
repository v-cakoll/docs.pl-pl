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
ms.openlocfilehash: 29097dc4aa0bf712b9b2beda4450820a66472ba7
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43891522"
---
# <a name="-operator-c-reference"></a>() — Operator (odwołanie w C#)
Oprócz określania kolejności operacji w wyrażeniach nawiasy są też używane do następujących zadań:  
  
1.  Określanie rzutowania lub konwersji typów.  
  
     [!code-csharp[csRefOperators#1](../../../csharp/language-reference/operators/codesnippet/CSharp/invocation-operator_1.cs)]  
  
2.  Wywoływanie metody lub delegatów.  
  
     [!code-csharp[csRefOperators#2](../../../csharp/language-reference/operators/codesnippet/CSharp/invocation-operator_2.cs)]  
  
## <a name="remarks"></a>Uwagi  
 Rzutowanie jawnie wywołuje operatora konwersji z jednego typu do drugiego. Rzutowanie kończy się niepowodzeniem, jeśli żaden operator konwersji nie jest zdefiniowany. Aby zdefiniować operatora konwersji, zobacz [jawne](../../../csharp/language-reference/keywords/explicit.md) i [niejawne](../../../csharp/language-reference/keywords/implicit.md) definiowanie operatorów konwersji.  
  
 Operator `()` nie może być przeciążony.  
  
 Aby uzyskać więcej informacji, zobacz [Rzutowanie i konwersje typów](../../../csharp/programming-guide/types/casting-and-type-conversions.md).   
  
 Aby uzyskać więcej informacji na temat wywołania metody, zobacz [metody](../../../csharp/programming-guide/classes-and-structs/methods.md).  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Dokumentacja języka C#](../../../csharp/language-reference/index.md)  
- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
- [Operatory języka C#](../../../csharp/language-reference/operators/index.md)
