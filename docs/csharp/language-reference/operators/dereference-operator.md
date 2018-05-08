---
title: -&gt;Operator (odwołanie w C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- ->_CSharpKeyword
helpviewer_keywords:
- member access operator (->) [C#]
- -> operator [C#]
ms.assetid: e39ccdc1-f1ff-4a92-bf1d-ac2c8c11316a
caps.latest.revision: 19
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 4c5918f56257feb29d2624ba29b8cebaaa4f4ebe
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="-gt-operator-c-reference"></a>-&gt;Operator (odwołanie w C#)
Operator `->` laczy wyluskanie wskaznika i dostep do elementu czlonkowskiego.  
  
## <a name="remarks"></a>Uwagi  
 Wyrażenie w postaci  
  
```  
x->y  
```  
  
 (gdzie `x` to wskaznik typu `T*`, a `y` to element czlonkowski `T`) jest odpowiednikiem wyrazenia  
  
```  
(*x).y  
```  
  
 Operatora `->` mozna uzywac tylko w kodzie, który jest oznaczony jako [niebezpieczny](../../../csharp/language-reference/keywords/unsafe.md).  
  
 Operator `->` nie może być przeciążony.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csRefOperators#15](../../../csharp/language-reference/operators/codesnippet/CSharp/dereference-operator_1.cs)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Operatory C#](../../../csharp/language-reference/operators/index.md)
