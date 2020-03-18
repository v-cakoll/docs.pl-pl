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
# <a name="elif-c-reference"></a><span data-ttu-id="58602-102">#elif (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="58602-102">#elif (C# Reference)</span></span>
<span data-ttu-id="58602-103">`#elif`umożliwia utworzenie złożonej dyrektywy warunkowej.</span><span class="sxs-lookup"><span data-stu-id="58602-103">`#elif` lets you create a compound conditional directive.</span></span> <span data-ttu-id="58602-104">Wyrażenie `#elif` zostanie obliczone, jeśli ani poprzedni [#if,](./preprocessor-if.md) ani żadne `#elif` poprzednie, opcjonalne wyrażenia dyrektywy nie będą oceniane jako `true`.</span><span class="sxs-lookup"><span data-stu-id="58602-104">The `#elif` expression will be evaluated if neither the preceding [#if](./preprocessor-if.md) nor any preceding, optional, `#elif` directive expressions evaluate to `true`.</span></span> <span data-ttu-id="58602-105">Jeśli `#elif` wyrażenie ocenia `true`, kompilator ocenia cały `#elif` kod między i następnej dyrektywy warunkowej.</span><span class="sxs-lookup"><span data-stu-id="58602-105">If a `#elif` expression evaluates to `true`, the compiler evaluates all the code between the `#elif` and the next conditional directive.</span></span> <span data-ttu-id="58602-106">Przykład:</span><span class="sxs-lookup"><span data-stu-id="58602-106">For example:</span></span>  
  
```csharp
#define VC7  
//...  
#if debug  
    Console.WriteLine("Debug build");  
#elif VC7  
    Console.WriteLine("Visual Studio 7");  
#endif  
```  
  
 <span data-ttu-id="58602-107">Można użyć operatorów `==` (równości), `!=` (nierówności), `&&` (i) i `||` (lub), aby ocenić wiele symboli.</span><span class="sxs-lookup"><span data-stu-id="58602-107">You can use the operators `==` (equality), `!=` (inequality), `&&` (and), and `||` (or), to evaluate multiple symbols.</span></span> <span data-ttu-id="58602-108">Można również grupować symbole i operatory z nawiasami.</span><span class="sxs-lookup"><span data-stu-id="58602-108">You can also group symbols and operators with parentheses.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="58602-109">Uwagi</span><span class="sxs-lookup"><span data-stu-id="58602-109">Remarks</span></span>  
 <span data-ttu-id="58602-110">`#elif`odpowiada wykorzystaniu:</span><span class="sxs-lookup"><span data-stu-id="58602-110">`#elif` is equivalent to using:</span></span>  
  
```csharp
#else  
#if  
```  
  
 <span data-ttu-id="58602-111">Korzystanie `#elif` jest prostsze, `#if` ponieważ każdy wymaga [#endif](./preprocessor-endif.md), podczas `#elif` gdy może być używany bez dopasowania `#endif`.</span><span class="sxs-lookup"><span data-stu-id="58602-111">Using `#elif` is simpler, because each `#if` requires a [#endif](./preprocessor-endif.md), whereas a `#elif` can be used without a matching `#endif`.</span></span>  
  
 <span data-ttu-id="58602-112">Zobacz [#if](./preprocessor-if.md) przykład użycia `#elif`.</span><span class="sxs-lookup"><span data-stu-id="58602-112">See [#if](./preprocessor-if.md) for an example of how to use `#elif`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="58602-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="58602-113">See also</span></span>

- [<span data-ttu-id="58602-114">Odwołanie do języka C#</span><span class="sxs-lookup"><span data-stu-id="58602-114">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="58602-115">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="58602-115">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="58602-116">Dyrektywy przedprocesorowe C#</span><span class="sxs-lookup"><span data-stu-id="58602-116">C# Preprocessor Directives</span></span>](./index.md)
