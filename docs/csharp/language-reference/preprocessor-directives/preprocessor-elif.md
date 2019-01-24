---
title: '#elif — C# odwołania'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '#elif'
helpviewer_keywords:
- '#elif directive [C#]'
ms.assetid: 731d78df-08e0-4d51-b8c8-f193c27de13f
ms.openlocfilehash: 00a9298be6ecd6f5e775d930190ddb6e227e4711
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54587232"
---
# <a name="elif-c-reference"></a>#elif (odwołanie w C#)
Dyrektywa `#elif` umożliwia tworzenie złożonych dyrektyw warunkowych. Wyrażenie dyrektywy `#elif` zostanie oszacowane, jeśli żadne z wcześniejszych wyrażeń [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) ani (opcjonalnie) żadne z wcześniejszych wyrażeń `#elif` nie zwróci wyniku `true`. Jeżeli wyrażenie `#elif` zwraca w wyniku `true`, kompilator wykonuje cały kod między dyrektywą `#elif` a następną dyrektywą warunkową. Na przykład:  
  
```csharp
#define VC7  
//...  
#if debug  
    Console.WriteLine("Debug build");  
#elif VC7  
    Console.WriteLine("Visual Studio 7");  
#endif  
```  
  
 Można używać operatorów `==` (równość), `!=` (nierówność), `&&` (oraz) `||` (lub), aby szacować wiele symboli. Można także grupować symbole i operatory za pomocą nawiasów. Można także grupować symboli i operatorów, za pomocą nawiasów.  
  
## <a name="remarks"></a>Uwagi  
 Użycie `#elif` jest równoważne z użyciem:  
  
```csharp
#else  
#if  
```  
  
 Użycie dyrektywy `#elif` jest łatwiejsze, ponieważ każda dyrektywa `#if` wymaga dyrektywy [#endif](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md), podczas gdy dyrektywa `#elif` może być używana bez odpowiadającej jej dyrektywy `#endif`.  
  
 Aby zapoznać się z przykładem użycia dyrektywy [, zobacz ](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md)#if`#elif`.  
  
## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../../../csharp/language-reference/index.md)
- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)
- [Dyrektywy preprocesora C#](../../../csharp/language-reference/preprocessor-directives/index.md)
