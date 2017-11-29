---
title: "#<a name=\"elif-c-reference\"></a>elif (odwołanie w C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: '#elif'
helpviewer_keywords: '#elif directive [C#]'
ms.assetid: 731d78df-08e0-4d51-b8c8-f193c27de13f
caps.latest.revision: "14"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 1512bbbc46ce15570507c8b51540eef607d55dc8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="elif-c-reference"></a>#elif (odwołanie w C#)
`#elif`Umożliwia tworzenie złożonego dyrektywy warunkowej. `#elif` Jeśli nie zostanie obliczone wyrażenie poprzedniego [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) lub any poprzedzających, opcjonalnie, `#elif` wynikiem obliczania wyrażenia dyrektywy `true`. Jeśli `#elif` wyrażenie daje w wyniku `true`, kompilator ocenia cały kod między `#elif` i dalej dyrektywy warunkowej. Na przykład:  
  
```csharp
#define VC7  
//...  
#if debug  
    Console.Writeline("Debug build");  
#elif VC7  
    Console.Writeline("Visual Studio 7");  
#endif  
```  
  
 Można używać operatorów `==` (równości) `!=` (nierówność), `&&` (a) i `||` (lub), aby ocenić wiele symboli. Można także grupować symbole i operatory w nawiasach.  
  
## <a name="remarks"></a>Uwagi  
 `#elif`odpowiada za pomocą:  
  
```csharp
#else  
#if  
```  
  
 Przy użyciu `#elif` jest łatwiejsze, ponieważ każdy `#if` wymaga [#endif](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md), podczas gdy `#elif` może być używany bez odpowiadającego mu `#endif`.  
  
 Zobacz [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) przykład sposobu użycia `#elif`.  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Dyrektywy preprocesora C#](../../../csharp/language-reference/preprocessor-directives/index.md)
