---
title: Operator ~ (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- ~_CSharpKeyword
helpviewer_keywords:
- tilde (~) one's complement operator [C#]
- ~ operator [C#]
- ~ [C#], bitwise complement operator
- bitwise complement operator [C#]
ms.assetid: 11bc078a-50e2-4d7e-9896-67ef669dc602
ms.openlocfilehash: 25b157fafde7d2b75cd8b112848a01e9b3fb0db2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="-operator-c-reference"></a>Operator ~ (odwołanie w C#)
Operator `~` wykonuje operację dopełnienia bitowego na jego argumencie operacji, która powoduje odwrócenie każdego z bitów. Operatory dopełnienia bitowego są wstępnie zdefiniowane dla następujących typów: [int](../../../csharp/language-reference/keywords/int.md), [uint](../../../csharp/language-reference/keywords/uint.md), [długi](../../../csharp/language-reference/keywords/long.md), i [ulong](../../../csharp/language-reference/keywords/ulong.md).
  
> [!NOTE]
> Symbol `~` służy również do deklarowania finalizatorów. Aby uzyskać więcej informacji, zobacz [finalizatory](../../../csharp/programming-guide/classes-and-structs/destructors.md).  
  
## <a name="remarks"></a>Uwagi  
 Typy definiowane przez użytkownika mogą przeciążać operator `~`. Aby uzyskać więcej informacji, zobacz [operator](../../../csharp/language-reference/keywords/operator.md). Operacje na typach całkowitych są zazwyczaj dozwolone na wyliczeniach.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csRefOperators#25](../../../csharp/language-reference/operators/codesnippet/CSharp/bitwise-complement-operator_1.cs)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Operatory języka C#](../../../csharp/language-reference/operators/index.md)  
 [Finalizatory](../../../csharp/programming-guide/classes-and-structs/destructors.md)
