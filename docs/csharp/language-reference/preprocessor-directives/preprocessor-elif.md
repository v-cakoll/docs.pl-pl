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
# <a name="elif-c-reference"></a><span data-ttu-id="7f0cd-102">#elif (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="7f0cd-102">#elif (C# Reference)</span></span>
<span data-ttu-id="7f0cd-103">Dyrektywa `#elif` umożliwia tworzenie złożonych dyrektyw warunkowych.</span><span class="sxs-lookup"><span data-stu-id="7f0cd-103">`#elif` lets you create a compound conditional directive.</span></span> <span data-ttu-id="7f0cd-104">Wyrażenie dyrektywy `#elif` zostanie oszacowane, jeśli żadne z wcześniejszych wyrażeń [#if](./preprocessor-if.md) ani (opcjonalnie) żadne z wcześniejszych wyrażeń `#elif` nie zwróci wyniku `true`.</span><span class="sxs-lookup"><span data-stu-id="7f0cd-104">The `#elif` expression will be evaluated if neither the preceding [#if](./preprocessor-if.md) nor any preceding, optional, `#elif` directive expressions evaluate to `true`.</span></span> <span data-ttu-id="7f0cd-105">Jeżeli wyrażenie `#elif` zwraca w wyniku `true`, kompilator wykonuje cały kod między dyrektywą `#elif` a następną dyrektywą warunkową.</span><span class="sxs-lookup"><span data-stu-id="7f0cd-105">If a `#elif` expression evaluates to `true`, the compiler evaluates all the code between the `#elif` and the next conditional directive.</span></span> <span data-ttu-id="7f0cd-106">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="7f0cd-106">For example:</span></span>  
  
```csharp
#define VC7  
//...  
#if debug  
    Console.WriteLine("Debug build");  
#elif VC7  
    Console.WriteLine("Visual Studio 7");  
#endif  
```  
  
 <span data-ttu-id="7f0cd-107">Można używać operatorów `==` (równość), `!=` (nierówność), `&&` (oraz) `||` (lub), aby szacować wiele symboli. Można także grupować symbole i operatory za pomocą nawiasów.</span><span class="sxs-lookup"><span data-stu-id="7f0cd-107">You can use the operators `==` (equality), `!=` (inequality), `&&` (and), and `||` (or), to evaluate multiple symbols.</span></span> <span data-ttu-id="7f0cd-108">Można również grupować symbole i operatory za pomocą nawiasów.</span><span class="sxs-lookup"><span data-stu-id="7f0cd-108">You can also group symbols and operators with parentheses.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7f0cd-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="7f0cd-109">Remarks</span></span>  
 <span data-ttu-id="7f0cd-110">Użycie `#elif` jest równoważne z użyciem:</span><span class="sxs-lookup"><span data-stu-id="7f0cd-110">`#elif` is equivalent to using:</span></span>  
  
```csharp
#else  
#if  
```  
  
 <span data-ttu-id="7f0cd-111">Użycie dyrektywy `#elif` jest łatwiejsze, ponieważ każda dyrektywa `#if` wymaga dyrektywy [#endif](./preprocessor-endif.md), podczas gdy dyrektywa `#elif` może być używana bez odpowiadającej jej dyrektywy `#endif`.</span><span class="sxs-lookup"><span data-stu-id="7f0cd-111">Using `#elif` is simpler, because each `#if` requires a [#endif](./preprocessor-endif.md), whereas a `#elif` can be used without a matching `#endif`.</span></span>  
  
 <span data-ttu-id="7f0cd-112">Aby zapoznać się z przykładem użycia dyrektywy [, zobacz ](./preprocessor-if.md)#if`#elif`.</span><span class="sxs-lookup"><span data-stu-id="7f0cd-112">See [#if](./preprocessor-if.md) for an example of how to use `#elif`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7f0cd-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7f0cd-113">See also</span></span>

- [<span data-ttu-id="7f0cd-114">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="7f0cd-114">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="7f0cd-115">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="7f0cd-115">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="7f0cd-116">Dyrektywy preprocesora C#</span><span class="sxs-lookup"><span data-stu-id="7f0cd-116">C# Preprocessor Directives</span></span>](./index.md)
