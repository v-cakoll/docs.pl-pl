---
title: Operator *= (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- '*=_CSharpKeyword'
helpviewer_keywords:
- '*= operator [C#]'
- binary multiplication assignment operator (*=) [C#]
ms.assetid: 2e472155-59db-4dbf-bb94-bcccfa1a794d
ms.openlocfilehash: 6bbf2142ca7e9e05010a29920da52e1439f6e882
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2018
---
# <a name="-operator-c-reference"></a>Operator *= (odwołanie w C#)
Operator przypisania mnożenia danych binarnych.  
  
## <a name="remarks"></a>Uwagi  
 Wyrażenie używające operatora przypisania `*=`, takie jak  
  
```csharp  
x *= y  
```  
  
 odpowiada wyrażeniu  
  
```csharp  
x = x * y  
```  
  
 z tą różnicą, że `x` jest obliczany tylko raz. [Operator *](../../../csharp/language-reference/operators/multiplication-operator.md) jest wstępnie zdefiniowany dla typów liczbowych do wykonania mnożenia.  
  
 Operator `*=` nie może zostać przeciążony bezpośrednio, ale typy danych zdefiniowane przez użytkownika mogą przeciążać [operator *](../../../csharp/language-reference/operators/multiplication-operator.md) (zobacz [operator](../../../csharp/language-reference/keywords/operator.md)).  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csRefOperators#13](../../../csharp/language-reference/operators/codesnippet/CSharp/multiplication-assignment-operator_1.cs)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Operatory języka C#](../../../csharp/language-reference/operators/index.md)
