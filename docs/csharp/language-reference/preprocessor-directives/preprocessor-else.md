---
title: '#else (odwołanie w C#)'
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '#else'
helpviewer_keywords:
- '#else directive [C#]'
ms.assetid: 6a347322-cfa2-4a86-98f8-ddfa2cb7d4db
caps.latest.revision: 11
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c3468d35a6e45c06f46fe8671708ce01a3cc7b65
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="else-c-reference"></a><span data-ttu-id="65ad0-102">#else (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="65ad0-102">#else (C# Reference)</span></span>
<span data-ttu-id="65ad0-103">`#else`umożliwia utworzenie złożonej dyrektywy warunkowej polegającej na tym, że jeśli żadne z wyrażeń we wcześniejszych dyrektywach [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) i (opcjonalnie) [#elif](../../../csharp/language-reference/preprocessor-directives/preprocessor-elif.md) nie zwróci wartości `true`, kompilator wykona kod między dyrektywą`#else` a następującą po niej dyrektywą`#endif`.</span><span class="sxs-lookup"><span data-stu-id="65ad0-103">`#else` lets you create a compound conditional directive, so that, if none of the expressions in the preceding [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) or (optional) [#elif](../../../csharp/language-reference/preprocessor-directives/preprocessor-elif.md) directives to `true`, the compiler will evaluate all code between `#else` and the subsequent `#endif`.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="65ad0-104">Uwagi</span><span class="sxs-lookup"><span data-stu-id="65ad0-104">Remarks</span></span>  
 <span data-ttu-id="65ad0-105">Następną dyrektywą preprocesora po [ musi być ](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md)#endif`#else`.</span><span class="sxs-lookup"><span data-stu-id="65ad0-105">[#endif](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md) must be the next preprocessor directive after `#else`.</span></span> <span data-ttu-id="65ad0-106">Aby zapoznać się z przykładem użycia dyrektywy [, zobacz ](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md)#if`#else`.</span><span class="sxs-lookup"><span data-stu-id="65ad0-106">See [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) for an example of how to use `#else`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="65ad0-107">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="65ad0-107">See Also</span></span>  
 [<span data-ttu-id="65ad0-108">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="65ad0-108">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="65ad0-109">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="65ad0-109">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="65ad0-110">Dyrektywy preprocesora C#</span><span class="sxs-lookup"><span data-stu-id="65ad0-110">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)
