---
title: "#<a name=\"endif-c-reference\"></a>ENDIF (odwołanie w C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: '#endif'
helpviewer_keywords: '#endif directive [C#]'
ms.assetid: 6a5fca55-5aee-441f-86f6-1c99fbe9ec05
caps.latest.revision: "9"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: d7e68dd20d914052c3fe5cabcb83abdae100465c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="endif-c-reference"></a><span data-ttu-id="9f170-102">#endif (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="9f170-102">#endif (C# Reference)</span></span>
<span data-ttu-id="9f170-103">`#endif`Określa koniec dyrektywy warunkowej, rozpoczął się [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) dyrektywy.</span><span class="sxs-lookup"><span data-stu-id="9f170-103">`#endif` specifies the end of a conditional directive, which began with the [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) directive.</span></span> <span data-ttu-id="9f170-104">Na przykład</span><span class="sxs-lookup"><span data-stu-id="9f170-104">For example,</span></span>  
  
```csharp
#define DEBUG  
// ...  
#if DEBUG  
    Console.WriteLine("Debug version");  
#endif  
```  
  
## <a name="remarks"></a><span data-ttu-id="9f170-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9f170-105">Remarks</span></span>  
 <span data-ttu-id="9f170-106">Dyrektywy warunkowej, począwszy od `#if` dyrektywy, musi być jawnie zakończona z `#endif` dyrektywy.</span><span class="sxs-lookup"><span data-stu-id="9f170-106">A conditional directive, beginning with a `#if` directive, must explicitly be terminated with a `#endif` directive.</span></span> <span data-ttu-id="9f170-107">Zobacz [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) przykład sposobu użycia `#endif`.</span><span class="sxs-lookup"><span data-stu-id="9f170-107">See [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) for an example of how to use `#endif`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f170-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9f170-108">See Also</span></span>  
 [<span data-ttu-id="9f170-109">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="9f170-109">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="9f170-110">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="9f170-110">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="9f170-111">Dyrektywy preprocesora C#</span><span class="sxs-lookup"><span data-stu-id="9f170-111">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)
