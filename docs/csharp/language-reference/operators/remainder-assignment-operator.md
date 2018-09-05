---
title: Operator %= (odwołanie w C#)
ms.date: 04/04/2018
f1_keywords:
- '%=_CSharpKeyword'
helpviewer_keywords:
- remainder assignment operator (%=) [C#]
- '%= assignment operator (remainder assignment) [C#]'
ms.assetid: 47e5f068-1d97-4010-bd3b-e21b5d3a77f5
ms.openlocfilehash: 009c162b13fab05ba349d0535fe8dfae206502f3
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43507940"
---
# <a name="-operator-c-reference"></a>Operator %= (odwołanie w C#)
Operator przypisania reszty.  
  
## <a name="remarks"></a>Uwagi  
 Wyrażenie używające operatora przypisania `%=`, takie jak  
  
```csharp  
x %= y  
```  
  
 odpowiada wyrażeniu  
  
```csharp  
x = x % y  
```  
  
 z tą różnicą, że `x` jest obliczany tylko raz. [% — Operator](../../../csharp/language-reference/operators/remainder-operator.md) wstępnie zdefiniowany dla typów liczbowych do obliczania pozostałej po dzielenia.  
  
 `%=` Operator nie może zostać przeciążony bezpośrednio, ale typy zdefiniowane przez użytkownika może doprowadzić do przeciążenia [operatora %](../../../csharp/language-reference/operators/remainder-operator.md) (zobacz [— operator (odwołanie w C#)](../../../csharp/language-reference/keywords/operator.md)).  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csRefOperators#4](../../../csharp/language-reference/operators/codesnippet/CSharp/modulus-assignment-operator_1.cs)]  
  
## <a name="see-also"></a>Zobacz też

- [Dokumentacja języka C#](../../../csharp/language-reference/index.md)  
- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
- [Operatory języka C#](../../../csharp/language-reference/operators/index.md)
