---
title: '#elif (odwołanie w C#)'
ms.date: 07/20/2015
f1_keywords:
- '#elif'
helpviewer_keywords:
- '#elif directive [C#]'
ms.assetid: 731d78df-08e0-4d51-b8c8-f193c27de13f
ms.openlocfilehash: c6d797b68ad03023d6101b20cacae6d828abe0c1
ms.sourcegitcommit: a1e35d4e94edab384a63406c0a5438306873031b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2018
ms.locfileid: "42753931"
---
# <a name="elif-c-reference"></a><span data-ttu-id="0974d-102">#elif (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="0974d-102">#elif (C# Reference)</span></span>
<span data-ttu-id="0974d-103">Dyrektywa `#elif` umożliwia tworzenie złożonych dyrektyw warunkowych.</span><span class="sxs-lookup"><span data-stu-id="0974d-103">`#elif` lets you create a compound conditional directive.</span></span> <span data-ttu-id="0974d-104">Wyrażenie dyrektywy `#elif` zostanie oszacowane, jeśli żadne z wcześniejszych wyrażeń [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) ani (opcjonalnie) żadne z wcześniejszych wyrażeń `#elif` nie zwróci wyniku `true`.</span><span class="sxs-lookup"><span data-stu-id="0974d-104">The `#elif` expression will be evaluated if neither the preceding [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) nor any preceding, optional, `#elif` directive expressions evaluate to `true`.</span></span> <span data-ttu-id="0974d-105">Jeżeli wyrażenie `#elif` zwraca w wyniku `true`, kompilator wykonuje cały kod między dyrektywą `#elif` a następną dyrektywą warunkową.</span><span class="sxs-lookup"><span data-stu-id="0974d-105">If a `#elif` expression evaluates to `true`, the compiler evaluates all the code between the `#elif` and the next conditional directive.</span></span> <span data-ttu-id="0974d-106">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="0974d-106">For example:</span></span>  
  
```csharp
#define VC7  
//...  
#if debug  
    Console.WriteLine("Debug build");  
#elif VC7  
    Console.WriteLine("Visual Studio 7");  
#endif  
```  
  
 <span data-ttu-id="0974d-107">Można używać operatorów `==` (równość), `!=` (nierówność), `&&` (oraz) `||` (lub), aby szacować wiele symboli. Można także grupować symbole i operatory za pomocą nawiasów.</span><span class="sxs-lookup"><span data-stu-id="0974d-107">You can use the operators `==` (equality), `!=` (inequality), `&&` (and), and `||` (or), to evaluate multiple symbols.</span></span> <span data-ttu-id="0974d-108">Można także grupować symboli i operatorów, za pomocą nawiasów.</span><span class="sxs-lookup"><span data-stu-id="0974d-108">You can also group symbols and operators with parentheses.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="0974d-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="0974d-109">Remarks</span></span>  
 <span data-ttu-id="0974d-110">Użycie `#elif` jest równoważne z użyciem:</span><span class="sxs-lookup"><span data-stu-id="0974d-110">`#elif` is equivalent to using:</span></span>  
  
```csharp
#else  
#if  
```  
  
 <span data-ttu-id="0974d-111">Użycie dyrektywy `#elif` jest łatwiejsze, ponieważ każda dyrektywa `#if` wymaga dyrektywy [#endif](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md), podczas gdy dyrektywa `#elif` może być używana bez odpowiadającej jej dyrektywy `#endif`.</span><span class="sxs-lookup"><span data-stu-id="0974d-111">Using `#elif` is simpler, because each `#if` requires a [#endif](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md), whereas a `#elif` can be used without a matching `#endif`.</span></span>  
  
 <span data-ttu-id="0974d-112">Aby zapoznać się z przykładem użycia dyrektywy [, zobacz ](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md)#if`#elif`.</span><span class="sxs-lookup"><span data-stu-id="0974d-112">See [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) for an example of how to use `#elif`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0974d-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0974d-113">See Also</span></span>  
 [<span data-ttu-id="0974d-114">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="0974d-114">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="0974d-115">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="0974d-115">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="0974d-116">Dyrektywy preprocesora C#</span><span class="sxs-lookup"><span data-stu-id="0974d-116">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)
