---
title: Operator *= (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- '*=_CSharpKeyword'
helpviewer_keywords:
- '*= operator [C#]'
- binary multiplication assignment operator (*=) [C#]
ms.assetid: 2e472155-59db-4dbf-bb94-bcccfa1a794d
ms.openlocfilehash: e47bc5c681c94ac3fc5c345c56b3814350ffa5ec
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/26/2018
ms.locfileid: "42932353"
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

- [Dokumentacja języka C#](../../../csharp/language-reference/index.md)  
- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
- [Operatory języka C#](../../../csharp/language-reference/operators/index.md)
