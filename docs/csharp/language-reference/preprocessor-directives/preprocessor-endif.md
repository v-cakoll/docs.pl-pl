---
title: '#ENDIF (odwołanie w C#)'
ms.date: 07/20/2015
f1_keywords:
- '#endif'
helpviewer_keywords:
- '#endif directive [C#]'
ms.assetid: 6a5fca55-5aee-441f-86f6-1c99fbe9ec05
ms.openlocfilehash: 1686e706ce5cae3b2eaa28a7e1c89b5694b2be88
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33269980"
---
# <a name="endif-c-reference"></a><span data-ttu-id="88fed-102">#endif (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="88fed-102">#endif (C# Reference)</span></span>
<span data-ttu-id="88fed-103">`#endif` Określa koniec dyrektywy warunkowej, rozpoczął się [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) dyrektywy.</span><span class="sxs-lookup"><span data-stu-id="88fed-103">`#endif` specifies the end of a conditional directive, which began with the [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) directive.</span></span> <span data-ttu-id="88fed-104">Na przykład</span><span class="sxs-lookup"><span data-stu-id="88fed-104">For example,</span></span>  
  
```csharp
#define DEBUG  
// ...  
#if DEBUG  
    Console.WriteLine("Debug version");  
#endif  
```  
  
## <a name="remarks"></a><span data-ttu-id="88fed-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="88fed-105">Remarks</span></span>  
 <span data-ttu-id="88fed-106">Dyrektywy warunkowej, począwszy od `#if` dyrektywy, musi być jawnie zakończona z `#endif` dyrektywy.</span><span class="sxs-lookup"><span data-stu-id="88fed-106">A conditional directive, beginning with a `#if` directive, must explicitly be terminated with a `#endif` directive.</span></span> <span data-ttu-id="88fed-107">Aby zapoznać się z przykładem użycia dyrektywy [, zobacz ](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md)#if`#endif`.</span><span class="sxs-lookup"><span data-stu-id="88fed-107">See [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) for an example of how to use `#endif`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88fed-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="88fed-108">See Also</span></span>  
 [<span data-ttu-id="88fed-109">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="88fed-109">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="88fed-110">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="88fed-110">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="88fed-111">Dyrektywy preprocesora C#</span><span class="sxs-lookup"><span data-stu-id="88fed-111">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)
