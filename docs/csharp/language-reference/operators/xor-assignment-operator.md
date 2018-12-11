---
title: ^ = — Operator - C# odwołania
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- ^=_CSharpKeyword
helpviewer_keywords:
- ^= operator [C#]
ms.assetid: 3658ff9a-61cd-467e-ad6b-8fbf1cfbaae4
ms.openlocfilehash: cf39c8e8586e9d4f537fe38d8b28f55542db6ab8
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53237158"
---
# <a name="-operator-c-reference"></a>Operator ^= (odwołanie w C#)
Operator przypisania OR wyłączne.  
  
## <a name="remarks"></a>Uwagi  
 Wyrażenie formularza  
  
```csharp  
x ^= y  
```  
  
 jest wykonywane jako  
  
```csharp  
x = x ^ y  
```  
  
 z tą różnicą, że `x` jest obliczany tylko raz. [^ — Operator](../../../csharp/language-reference/operators/xor-operator.md) wykonuje OR wyłączne operacja bitowa na operandach typu całkowitego i logiczne OR wyłączne na [bool](../../../csharp/language-reference/keywords/bool.md) argumentów operacji.  
  
 ^ = — Operator nie może zostać przeciążony bezpośrednio, ale typy zdefiniowane przez użytkownika może doprowadzić do przeciążenia [^ — operator](../../../csharp/language-reference/operators/xor-operator.md) (zobacz [operator](../../../csharp/language-reference/keywords/operator.md)).  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csRefOperators#23](../../../csharp/language-reference/operators/codesnippet/CSharp/xor-assignment-operator_1.cs)]  
  
## <a name="see-also"></a>Zobacz też

- [Dokumentacja języka C#](../../../csharp/language-reference/index.md)  
- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
- [Operatory języka C#](../../../csharp/language-reference/operators/index.md)
