---
title: "#elif (odwołanie w C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '#elif'
helpviewer_keywords:
- '#elif directive [C#]'
ms.assetid: 731d78df-08e0-4d51-b8c8-f193c27de13f
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 1512bbbc46ce15570507c8b51540eef607d55dc8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="elif-c-reference"></a>#elif (odwołanie w C#)
  `#elif`Umożliwia tworzenie złożonych dyrektyw warunkowych. Dyrektywa `#elif` wykonuje się, jeśli nie zostanie wykonane żadne z poprzednich wyrażeń [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) ,lub (opcjonalnie) żadne z poprzedzających wyrażeń `#elif` nie zwróci wyniku `true`. Jeżeli wyrażenie `#elif` zwraca w wyniku `true`, kompilator wykonuje cały kod między `#elif`, a następną dyrektywą warunkową. Na przykład:  
  
```csharp
#define VC7  
//...  
#if debug  
    Console.Writeline("Debug build");  
#elif VC7  
    Console.Writeline("Visual Studio 7");  
#endif  
```  
  
 Można używać operatorów `==` (równości) `!=` (nierówność), `&&` (a) i `||` (lub), aby ocenić wiele symboli. Można także grupować symbole i operatory za pomocą nawiasów.  
  
## <a name="remarks"></a>Uwagi  
 Użycie `#elif` jest równoważne z użyciem:  
  
```csharp
#else  
#if  
```  
  
 Użycie `#elif` jest łatwiejsze, ponieważ każdy `#if` wymaga [#endif](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md), podczas gdy `#elif` może być używany bez odpowiadającego mu `#endif`.  
  
 Zobacz [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) przykład sposobu użycia `#elif`.  
  
## <a name="see-also"></a>Zobacz też  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Dyrektywy preprocesora C#](../../../csharp/language-reference/preprocessor-directives/index.md)
