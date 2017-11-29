---
title: "Operator %= (odwołanie w C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: '%=_CSharpKeyword'
helpviewer_keywords:
- modulus assignment operator (=%) [C#]
- '%= assignment operator (modulus assignment) [C#]'
ms.assetid: 47e5f068-1d97-4010-bd3b-e21b5d3a77f5
caps.latest.revision: "20"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 9bafd0078153e29fbf923948d9b380d4795c3d35
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a>Operator %= (odwołanie w C#)
Operator przypisania reszty.  
  
## <a name="remarks"></a>Uwagi  
 Za pomocą wyrażenia `%=` operator przypisania, takich jak  
  
```  
x %= y  
```  
  
 jest równoważny  
  
```  
x = x % y  
```  
  
 z tą różnicą, że `x` jest tylko jeden raz obliczone. [% Operator](../../../csharp/language-reference/operators/modulus-operator.md) jest wstępnie zdefiniowane na typy liczbowe do obliczenia resztę po dzielenia.  
  
 `%=` Operator nie może zostać przeciążony bezpośrednio, ale typy danych zdefiniowane przez użytkownika można przeciążać [% operator](../../../csharp/language-reference/operators/modulus-operator.md) (zobacz [— operator (odwołanie w C#)](../../../csharp/language-reference/keywords/operator.md)).  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csRefOperators#4](../../../csharp/language-reference/operators/codesnippet/CSharp/modulus-assignment-operator_1.cs)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Operatory C#](../../../csharp/language-reference/operators/index.md)
