---
title: -&gt; Operator (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- ->_CSharpKeyword
helpviewer_keywords:
- member access operator (->) [C#]
- -> operator [C#]
ms.assetid: e39ccdc1-f1ff-4a92-bf1d-ac2c8c11316a
ms.openlocfilehash: fb95e508ce1339868723bcc3178851e8c1355c1f
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44190231"
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

- [Dokumentacja języka C#](../../../csharp/language-reference/index.md)  
- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
- [Operatory języka C#](../../../csharp/language-reference/operators/index.md)
