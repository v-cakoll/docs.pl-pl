---
title: '&gt;&gt;= — Operator - C# odwołania'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '>>=_CSharpKeyword'
helpviewer_keywords:
- right shift assignment operator (>>=) [C#]
- '>>= operator (right-shift assignment) [C#]'
ms.assetid: b593778c-b9b4-440d-8b29-c1ac22cb81c0
ms.openlocfilehash: aebc92ffb007db7b4950313874ebc2bf3c40615f
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53239449"
---
# <a name="gtgt-operator-c-reference"></a>&gt;&gt;= — Operator (odwołanie w C#)
Operator przypisania przesunięcia w prawo.  
  
## <a name="remarks"></a>Uwagi  
 Wyrażenie formularza  
  
```csharp  
x >>= y  
```  
  
 jest wykonywane jako  
  
```csharp  
x = x >> y  
```  
  
 z tą różnicą, że `x` jest obliczone tylko raz. [Operator >>](../../../csharp/language-reference/operators/right-shift-operator.md) przesuwa `x` w prawo o liczbę bitów określoną przez `y`.  
  
 Operatora [ nie można przeciążyć bezpośrednio, ale ](../../../csharp/language-reference/operators/right-shift-operator.md)operator >>[ (zobacz ](../../../csharp/language-reference/keywords/operator.md)operator) może zostać przeciążony w typach danych zdefiniowanych przez użytkownika.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csRefOperators#11](../../../csharp/language-reference/operators/codesnippet/CSharp/right-shift-assignment-operator_1.cs)]  
  
## <a name="see-also"></a>Zobacz też

- [Dokumentacja języka C#](../../../csharp/language-reference/index.md)  
- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
- [Operatory języka C#](../../../csharp/language-reference/operators/index.md)
