---
title: '|= — Operator (odwołanie w C#)'
ms.date: 07/20/2015
f1_keywords:
- '|=_CSharpKeyword'
helpviewer_keywords:
- OR assignment operator (|=) [C#]
- '|= operator (OR assignment) [C#]'
ms.assetid: 8315b8cf-dd15-402f-92f0-c7db931696ca
ms.openlocfilehash: fe56005ce94656b5e8a075cddfb91dc0da096cf7
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43408426"
---
# <a name="-operator-c-reference"></a>|= — Operator (odwołanie w C#)
Operator przypisania OR.  
  
## <a name="remarks"></a>Uwagi  
 Wyrażenie używające operatora przypisania `|=`, takie jak  
  
```csharp  
x |= y  
```  
  
 odpowiada wyrażeniu  
  
```csharp  
x = x | y  
```  
  
 z tą różnicą, że `x` jest obliczany tylko raz. [ &#124; Operator](../../../csharp/language-reference/operators/or-operator.md) wykonuje bitowe logicznej operacji lub w przypadku argumentów operacji typu całkowitego i operator logiczny lub w przypadku argumentów bool operacji.  
  
 `|=` Operator nie może zostać przeciążony bezpośrednio, ale typy zdefiniowane przez użytkownika może doprowadzić do przeciążenia [ &#124; operator](../../../csharp/language-reference/operators/or-operator.md) (zobacz [operator](../../../csharp/language-reference/keywords/operator.md)).  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csRefOperators#10](../../../csharp/language-reference/operators/codesnippet/CSharp/or-assignment-operator_1.cs)]  
  
## <a name="see-also"></a>Zobacz też

- [Dokumentacja języka C#](../../../csharp/language-reference/index.md)  
- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
- [Operatory języka C#](../../../csharp/language-reference/operators/index.md)
