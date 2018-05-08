---
title: Operator /= (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- /=_CSharpKeyword
helpviewer_keywords:
- division assignment operator (/=) [C#]
- /= (division assignment operator) [C#]
ms.assetid: 50fc02b0-ee9c-4c3e-b58d-d591282caf1c
ms.openlocfilehash: 1d9b918c66ce361067d906a055df5adb25a5a308
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="-operator-c-reference"></a>Operator /= (odwołanie w C#)
Operator przypisania dzielenia.  
  
## <a name="remarks"></a>Uwagi  
 Za pomocą wyrażenia `/=` operator przypisania, takich jak  
  
```  
x /= y  
```  
  
 jest równoważny  
  
```  
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
