---
title: / = — Operator - C# odwołania
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- /=_CSharpKeyword
helpviewer_keywords:
- division assignment operator (/=) [C#]
- /= (division assignment operator) [C#]
ms.assetid: 50fc02b0-ee9c-4c3e-b58d-d591282caf1c
ms.openlocfilehash: 0487088fa5420f2d15541aa3f7b1d4ec604195bb
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53241249"
---
# <a name="-operator-c-reference"></a>Operator /= (odwołanie w C#)
Operator przypisania dzielenia.  
  
## <a name="remarks"></a>Uwagi  
 Wyrażenie używające operatora przypisania `/=`, takie jak  
  
```csharp  
x /= y  
```  
  
 odpowiada wyrażeniu  
  
```csharp  
x = x / y  
```  
  
 z tą różnicą, że `x` jest obliczany tylko raz. [/ Operator](../../../csharp/language-reference/operators/division-operator.md) wstępnie zdefiniowany dla typów liczbowych wykonać dzielenie.  
  
 `/=` Operator nie może zostać przeciążony bezpośrednio, ale typy zdefiniowane przez użytkownika może doprowadzić do przeciążenia [/ operator](../../../csharp/language-reference/operators/division-operator.md) (zobacz [operator](../../../csharp/language-reference/keywords/operator.md)). Na wszystkich złożone operatory przypisania przeciążenie operatora binarnego niejawnie przeciążenia równoważne przypisania złożonego.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csRefOperators#5](codesnippet/CSharp/division-assignment-operator_1.cs)]  
  
## <a name="see-also"></a>Zobacz też

- [Dokumentacja języka C#](../../../csharp/language-reference/index.md)  
- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
- [Operatory języka C#](../../../csharp/language-reference/operators/index.md)
