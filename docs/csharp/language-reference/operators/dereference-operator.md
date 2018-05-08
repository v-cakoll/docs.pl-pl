---
title: -&gt; Operator (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- ->_CSharpKeyword
helpviewer_keywords:
- member access operator (->) [C#]
- -> operator [C#]
ms.assetid: e39ccdc1-f1ff-4a92-bf1d-ac2c8c11316a
ms.openlocfilehash: 09d67b8386da371f7d98a8171f60298b316091ea
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="-gt-operator-c-reference"></a>-&gt; Operator (odwołanie w C#)
`->` Łączy wskaźnik usuwania odwołania i element członkowski dostępu operatora.  
  
## <a name="remarks"></a>Uwagi  
 Wyrażenie w postaci  
  
```  
x->y  
```  
  
 (gdzie `x` wskaźnika typu `T*` i `y` jest elementem członkowskim `T`) jest odpowiednikiem,  
  
```  
(*x).y  
```  
  
 `->` Operatora można używać tylko w kodzie, który jest oznaczony jako [niebezpieczne](../../../csharp/language-reference/keywords/unsafe.md).  
  
 `->` Operator nie może być przeciążony.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[csRefOperators#15](../../../csharp/language-reference/operators/codesnippet/CSharp/dereference-operator_1.cs)]  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Operatory języka C#](../../../csharp/language-reference/operators/index.md)
