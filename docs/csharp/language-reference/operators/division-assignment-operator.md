---
title: Operator /= (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- /=_CSharpKeyword
helpviewer_keywords:
- division assignment operator (/=) [C#]
- /= (division assignment operator) [C#]
ms.assetid: 50fc02b0-ee9c-4c3e-b58d-d591282caf1c
ms.openlocfilehash: 8fff048cc441181aa3f0e3c0c638d501aaf9de3f
ms.sourcegitcommit: a368166a51e5204c0224fbf5e46476e3ed122817
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/31/2018
ms.locfileid: "43330935"
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
