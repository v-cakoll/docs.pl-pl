---
title: '#elif — C# odwołanie'
ms.date: 07/20/2015
f1_keywords:
- '#elif'
helpviewer_keywords:
- '#elif directive [C#]'
ms.assetid: 731d78df-08e0-4d51-b8c8-f193c27de13f
ms.openlocfilehash: c78818f40b76414d289af6c704ff019b63befe37
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712575"
---
# <a name="elif-c-reference"></a>#elif (odwołanie w C#)
Dyrektywa `#elif` umożliwia tworzenie złożonych dyrektyw warunkowych. Wyrażenie dyrektywy `#elif` zostanie oszacowane, jeśli żadne z wcześniejszych wyrażeń [#if](./preprocessor-if.md) ani (opcjonalnie) żadne z wcześniejszych wyrażeń `#elif` nie zwróci wyniku `true`. Jeżeli wyrażenie `#elif` zwraca w wyniku `true`, kompilator wykonuje cały kod między dyrektywą `#elif` a następną dyrektywą warunkową. Na przykład:  
  
```csharp
#define VC7  
//...  
#if debug  
    Console.WriteLine("Debug build");  
#elif VC7  
    Console.WriteLine("Visual Studio 7");  
#endif  
```  
  
 Można używać operatorów `==` (równość), `!=` (nierówność), `&&` (oraz) `||` (lub), aby szacować wiele symboli. Można także grupować symbole i operatory za pomocą nawiasów. Można również grupować symbole i operatory za pomocą nawiasów.  
  
## <a name="remarks"></a>Uwagi  
 Użycie `#elif` jest równoważne z użyciem:  
  
```csharp
#else  
#if  
```  
  
 Użycie dyrektywy `#elif` jest łatwiejsze, ponieważ każda dyrektywa `#if` wymaga dyrektywy [#endif](./preprocessor-endif.md), podczas gdy dyrektywa `#elif` może być używana bez odpowiadającej jej dyrektywy `#endif`.  
  
 Aby zapoznać się z przykładem użycia dyrektywy [, zobacz ](./preprocessor-if.md)#if`#elif`.  
  
## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Dyrektywy preprocesora C#](./index.md)
