---
title: '#elif - Odwołanie do języka C#'
ms.date: 07/20/2015
f1_keywords:
- '#elif'
helpviewer_keywords:
- '#elif directive [C#]'
ms.assetid: 731d78df-08e0-4d51-b8c8-f193c27de13f
ms.openlocfilehash: c78818f40b76414d289af6c704ff019b63befe37
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712575"
---
# <a name="elif-c-reference"></a>#elif (odwołanie w C#)
`#elif`umożliwia utworzenie złożonej dyrektywy warunkowej. Wyrażenie `#elif` zostanie obliczone, jeśli ani poprzedni [#if,](./preprocessor-if.md) ani żadne `#elif` poprzednie, opcjonalne wyrażenia dyrektywy nie będą oceniane jako `true`. Jeśli `#elif` wyrażenie ocenia `true`, kompilator ocenia cały `#elif` kod między i następnej dyrektywy warunkowej. Przykład:  
  
```csharp
#define VC7  
//...  
#if debug  
    Console.WriteLine("Debug build");  
#elif VC7  
    Console.WriteLine("Visual Studio 7");  
#endif  
```  
  
 Można użyć operatorów `==` (równości), `!=` (nierówności), `&&` (i) i `||` (lub), aby ocenić wiele symboli. Można również grupować symbole i operatory z nawiasami.  
  
## <a name="remarks"></a>Uwagi  
 `#elif`odpowiada wykorzystaniu:  
  
```csharp
#else  
#if  
```  
  
 Korzystanie `#elif` jest prostsze, `#if` ponieważ każdy wymaga [#endif](./preprocessor-endif.md), podczas `#elif` gdy może być używany bez dopasowania `#endif`.  
  
 Zobacz [#if](./preprocessor-if.md) przykład użycia `#elif`.  
  
## <a name="see-also"></a>Zobacz też

- [Odwołanie do języka C#](../index.md)
- [Przewodnik programowania języka C#](../../programming-guide/index.md)
- [Dyrektywy przedprocesorowe C#](./index.md)
