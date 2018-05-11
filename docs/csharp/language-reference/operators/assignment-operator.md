---
title: = — Operator (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- =_CSharpKeyword
helpviewer_keywords:
- = operator [C#]
ms.assetid: d802a6d5-32f0-42b8-b180-12f5a081bfc1
ms.openlocfilehash: 979250c91cfe2abdf7295ae3866cd6b4294285cf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="-operator-c-reference"></a>= — Operator (odwołanie w C#)
Operator przypisania (`=`) przechowuje wartość swojego prawostronnego argumentu operacji w lokalizacji przechowywania, właściwości lub indeksatorze wskazywanym przez jego lewostronny argument, a następnie zwraca wartość jako wynik. Argumenty operacji muszą być tego samego typu (lub prawostronny argument operacji musi umożliwiać konwersję na typ argumentu lewostronnego).
  
## <a name="remarks"></a>Uwagi  
 Operator przypisania nie może być przeciążony. Można jednak zdefiniować niejawne operatory konwersji typu, które umożliwiają korzystanie z operatora przypisania w połączeniu z tymi typami. Aby uzyskać więcej informacji, zobacz [Używanie operatorów konwersji](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md).
  
## <a name="example"></a>Przykład  
 [!code-csharp[csRefOperators#49](../../../csharp/language-reference/operators/codesnippet/CSharp/assignment-operator_1.cs)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Operatory języka C#](../../../csharp/language-reference/operators/index.md)
