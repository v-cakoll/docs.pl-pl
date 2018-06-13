---
title: Operator /= (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- /=_CSharpKeyword
helpviewer_keywords:
- division assignment operator (/=) [C#]
- /= (division assignment operator) [C#]
ms.assetid: 50fc02b0-ee9c-4c3e-b58d-d591282caf1c
ms.openlocfilehash: c31ff374e6af4c08c329a971fdd8af169e239395
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2018
ms.locfileid: "34171625"
---
# <a name="-operator-c-reference"></a>Operator /= (odwołanie w C#)
Operator przypisania dzielenia.  
  
## <a name="remarks"></a>Uwagi  
 Za pomocą wyrażenia `/=` operator przypisania, takich jak  
  
```csharp  
x /= y  
```  
  
 jest równoważny  
  
```csharp  
x = x / y  
```  
  
 z tą różnicą, że `x` jest tylko jeden raz obliczone. [/ — Operator](../../../csharp/language-reference/operators/division-operator.md) jest wstępnie zdefiniowane na typy liczbowe do wykonania podziału.  
  
 `/=` Operator nie może zostać przeciążony bezpośrednio, ale typy danych zdefiniowane przez użytkownika można przeciążać [/ — operator](../../../csharp/language-reference/operators/division-operator.md) (zobacz [operator](../../../csharp/language-reference/keywords/operator.md)). Na wszystkich złożone operatory przypisania niejawnie przeciążanie operatora binarnego overloads równoważne przydział złożony.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csRefOperators#5](codesnippet/CSharp/division-assignment-operator_1.cs)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Operatory języka C#](../../../csharp/language-reference/operators/index.md)
