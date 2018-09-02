---
title: '#else (odwołanie w C#)'
ms.date: 07/20/2015
f1_keywords:
- '#else'
helpviewer_keywords:
- '#else directive [C#]'
ms.assetid: 6a347322-cfa2-4a86-98f8-ddfa2cb7d4db
ms.openlocfilehash: 000cbaac4458a104214e3197442a21dcb4740a37
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43406157"
---
# <a name="else-c-reference"></a><span data-ttu-id="eede0-102">#else (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="eede0-102">#else (C# Reference)</span></span>
<span data-ttu-id="eede0-103">`#else` Umożliwia tworzenie złożonego dyrektywy warunkowej, tak, aby, jeśli żaden z wyrażeń w poprzednim [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) lub (opcjonalnie) [#elif](../../../csharp/language-reference/preprocessor-directives/preprocessor-elif.md) zwrócić dyrektywy `true`, kompilator ocenia wszystkie Kod między `#else` i kolejne `#endif`.</span><span class="sxs-lookup"><span data-stu-id="eede0-103">`#else` lets you create a compound conditional directive, so that, if none of the expressions in the preceding [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) or (optional) [#elif](../../../csharp/language-reference/preprocessor-directives/preprocessor-elif.md) directives evaluate to `true`, the compiler will evaluate all code between `#else` and the subsequent `#endif`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="eede0-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="eede0-104">Remarks</span></span>  
 <span data-ttu-id="eede0-105">Następną dyrektywą preprocesora po [ musi być ](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md)#endif`#else`.</span><span class="sxs-lookup"><span data-stu-id="eede0-105">[#endif](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md) must be the next preprocessor directive after `#else`.</span></span> <span data-ttu-id="eede0-106">Aby zapoznać się z przykładem użycia dyrektywy [, zobacz ](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md)#if`#else`.</span><span class="sxs-lookup"><span data-stu-id="eede0-106">See [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) for an example of how to use `#else`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eede0-107">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="eede0-107">See Also</span></span>

- [<span data-ttu-id="eede0-108">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="eede0-108">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="eede0-109">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="eede0-109">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="eede0-110">Dyrektywy preprocesora C#</span><span class="sxs-lookup"><span data-stu-id="eede0-110">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)
