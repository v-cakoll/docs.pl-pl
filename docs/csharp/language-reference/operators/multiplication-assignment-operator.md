---
title: "Operator *= (odwołanie w C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '*=_CSharpKeyword'
helpviewer_keywords:
- '*= operator [C#]'
- binary multiplication assignment operator (*=) [C#]
ms.assetid: 2e472155-59db-4dbf-bb94-bcccfa1a794d
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: dc2201f78e1e05bd0ccdea04522896c00294bdd6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a>Operator *= (odwołanie w C#)
Operator przypisania mnożenia danych binarnych.  
  
## <a name="remarks"></a>Uwagi  
 Za pomocą wyrażenia `*=` operator przypisania, takich jak  
  
```  
x *= y  
```  
  
 jest równoważny  
  
```  
x = x * y  
```  
  
 z tą różnicą, że `x` jest tylko jeden raz obliczone. [* — Operator](../../../csharp/language-reference/operators/multiplication-operator.md) jest wstępnie zdefiniowane na typy liczbowe do wykonania mnożenia.  
  
 `*=` Operator nie może zostać przeciążony bezpośrednio, ale typy danych zdefiniowane przez użytkownika można przeciążać [* — operator](../../../csharp/language-reference/operators/multiplication-operator.md) (zobacz [operator](../../../csharp/language-reference/keywords/operator.md)).  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csRefOperators#13](../../../csharp/language-reference/operators/codesnippet/CSharp/multiplication-assignment-operator_1.cs)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Operatory C#](../../../csharp/language-reference/operators/index.md)
