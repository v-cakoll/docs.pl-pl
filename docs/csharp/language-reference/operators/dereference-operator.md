---
title: -&gt; Operator (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- ->_CSharpKeyword
helpviewer_keywords:
- member access operator (->) [C#]
- -> operator [C#]
ms.assetid: e39ccdc1-f1ff-4a92-bf1d-ac2c8c11316a
ms.openlocfilehash: 037229b2081a43077cb4b5d02a8929b06ba9e077
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2018
---
# <a name="-gt-operator-c-reference"></a>-&gt; Operator (odwołanie w C#)
Operator `->` łączy wyłuskanie wskaźnika i dostęp do elementu członkowskiego.  
  
## <a name="remarks"></a>Uwagi  
 Wyrażenie w postaci  
  
```csharp  
x->y  
```  
  
 (gdzie `x` to wskaźnik typu `T*`, a `y` to element członkowski `T`) jest odpowiednikiem wyrażenia  
  
```csharp  
(*x).y  
```  
  
 Operatora `->` można używać tylko w kodzie, który jest oznaczony jako [niebezpieczny](../../../csharp/language-reference/keywords/unsafe.md).  
  
 Operator `->` nie może być przeciążony.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csRefOperators#15](../../../csharp/language-reference/operators/codesnippet/CSharp/dereference-operator_1.cs)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Operatory języka C#](../../../csharp/language-reference/operators/index.md)
