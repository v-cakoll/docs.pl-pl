---
title: '#ENDIF (odwołanie w C#)'
ms.date: 07/20/2015
f1_keywords:
- '#endif'
helpviewer_keywords:
- '#endif directive [C#]'
ms.assetid: 6a5fca55-5aee-441f-86f6-1c99fbe9ec05
ms.openlocfilehash: a652c1226f8f0c624ec8ebf0e665a4aa77ddf6f0
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43420817"
---
# <a name="endif-c-reference"></a><span data-ttu-id="9210e-102">#endif (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="9210e-102">#endif (C# Reference)</span></span>
<span data-ttu-id="9210e-103">`#endif` Określa koniec warunkowego dyrektywy, który rozpoczął się [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) dyrektywy.</span><span class="sxs-lookup"><span data-stu-id="9210e-103">`#endif` specifies the end of a conditional directive, which began with the [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) directive.</span></span> <span data-ttu-id="9210e-104">Na przykład</span><span class="sxs-lookup"><span data-stu-id="9210e-104">For example,</span></span>  
  
```csharp
#define DEBUG  
// ...  
#if DEBUG  
    Console.WriteLine("Debug version");  
#endif  
```  
  
## <a name="remarks"></a><span data-ttu-id="9210e-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="9210e-105">Remarks</span></span>  
 <span data-ttu-id="9210e-106">Dyrektywy warunkowej, począwszy od `#if` dyrektywy, jawnie muszą być zakończone znakiem `#endif` dyrektywy.</span><span class="sxs-lookup"><span data-stu-id="9210e-106">A conditional directive, beginning with a `#if` directive, must explicitly be terminated with a `#endif` directive.</span></span> <span data-ttu-id="9210e-107">Aby zapoznać się z przykładem użycia dyrektywy [, zobacz ](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md)#if`#endif`.</span><span class="sxs-lookup"><span data-stu-id="9210e-107">See [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) for an example of how to use `#endif`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9210e-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9210e-108">See Also</span></span>

- [<span data-ttu-id="9210e-109">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="9210e-109">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="9210e-110">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="9210e-110">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="9210e-111">Dyrektywy preprocesora C#</span><span class="sxs-lookup"><span data-stu-id="9210e-111">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)
