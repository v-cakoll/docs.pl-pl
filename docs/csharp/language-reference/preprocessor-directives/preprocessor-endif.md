---
title: '#ENDIF - C# odwołania'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '#endif'
helpviewer_keywords:
- '#endif directive [C#]'
ms.assetid: 6a5fca55-5aee-441f-86f6-1c99fbe9ec05
ms.openlocfilehash: 58e29363ca1298966ecf88e6b456f33f43a176b0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54573049"
---
# <a name="endif-c-reference"></a><span data-ttu-id="c0e6d-102">#endif (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="c0e6d-102">#endif (C# Reference)</span></span>
<span data-ttu-id="c0e6d-103">`#endif` Określa koniec warunkowego dyrektywy, który rozpoczął się [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) dyrektywy.</span><span class="sxs-lookup"><span data-stu-id="c0e6d-103">`#endif` specifies the end of a conditional directive, which began with the [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) directive.</span></span> <span data-ttu-id="c0e6d-104">Na przykład</span><span class="sxs-lookup"><span data-stu-id="c0e6d-104">For example,</span></span>  
  
```csharp
#define DEBUG  
// ...  
#if DEBUG  
    Console.WriteLine("Debug version");  
#endif  
```  
  
## <a name="remarks"></a><span data-ttu-id="c0e6d-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c0e6d-105">Remarks</span></span>  
 <span data-ttu-id="c0e6d-106">Dyrektywy warunkowej, począwszy od `#if` dyrektywy, jawnie muszą być zakończone znakiem `#endif` dyrektywy.</span><span class="sxs-lookup"><span data-stu-id="c0e6d-106">A conditional directive, beginning with a `#if` directive, must explicitly be terminated with a `#endif` directive.</span></span> <span data-ttu-id="c0e6d-107">Aby zapoznać się z przykładem użycia dyrektywy [, zobacz ](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md)#if`#endif`.</span><span class="sxs-lookup"><span data-stu-id="c0e6d-107">See [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) for an example of how to use `#endif`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c0e6d-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c0e6d-108">See also</span></span>

- [<span data-ttu-id="c0e6d-109">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="c0e6d-109">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="c0e6d-110">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="c0e6d-110">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="c0e6d-111">Dyrektywy preprocesora C#</span><span class="sxs-lookup"><span data-stu-id="c0e6d-111">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)
