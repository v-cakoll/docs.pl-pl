---
title: '#else — C# odwołania'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '#else'
helpviewer_keywords:
- '#else directive [C#]'
ms.assetid: 6a347322-cfa2-4a86-98f8-ddfa2cb7d4db
ms.openlocfilehash: eabbbb97c42af058c7426d4b72a53b41a96488ed
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53237366"
---
# <a name="else-c-reference"></a><span data-ttu-id="1725f-102">#else (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="1725f-102">#else (C# Reference)</span></span>
<span data-ttu-id="1725f-103">`#else` Umożliwia tworzenie złożonego dyrektywy warunkowej, tak, aby, jeśli żaden z wyrażeń w poprzednim [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) lub (opcjonalnie) [#elif](../../../csharp/language-reference/preprocessor-directives/preprocessor-elif.md) zwrócić dyrektywy `true`, kompilator ocenia wszystkie Kod między `#else` i kolejne `#endif`.</span><span class="sxs-lookup"><span data-stu-id="1725f-103">`#else` lets you create a compound conditional directive, so that, if none of the expressions in the preceding [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) or (optional) [#elif](../../../csharp/language-reference/preprocessor-directives/preprocessor-elif.md) directives evaluate to `true`, the compiler will evaluate all code between `#else` and the subsequent `#endif`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="1725f-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="1725f-104">Remarks</span></span>  
 <span data-ttu-id="1725f-105">Następną dyrektywą preprocesora po [ musi być ](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md)#endif`#else`.</span><span class="sxs-lookup"><span data-stu-id="1725f-105">[#endif](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md) must be the next preprocessor directive after `#else`.</span></span> <span data-ttu-id="1725f-106">Aby zapoznać się z przykładem użycia dyrektywy [, zobacz ](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md)#if`#else`.</span><span class="sxs-lookup"><span data-stu-id="1725f-106">See [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) for an example of how to use `#else`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1725f-107">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1725f-107">See Also</span></span>

- [<span data-ttu-id="1725f-108">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="1725f-108">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="1725f-109">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="1725f-109">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="1725f-110">Dyrektywy preprocesora C#</span><span class="sxs-lookup"><span data-stu-id="1725f-110">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)
