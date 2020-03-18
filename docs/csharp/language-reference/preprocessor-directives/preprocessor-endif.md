---
title: '#endif — odwołanie do języka C#'
ms.date: 07/20/2015
f1_keywords:
- '#endif'
helpviewer_keywords:
- '#endif directive [C#]'
ms.assetid: 6a5fca55-5aee-441f-86f6-1c99fbe9ec05
ms.openlocfilehash: cc344a224e2308e843328b228dd5e2466d02069f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712549"
---
# <a name="endif-c-reference"></a><span data-ttu-id="5e9d7-102">#endif (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="5e9d7-102">#endif (C# Reference)</span></span>
<span data-ttu-id="5e9d7-103">`#endif`określa koniec dyrektywy warunkowej, która rozpoczęła się od [dyrektywy #if.](./preprocessor-if.md)</span><span class="sxs-lookup"><span data-stu-id="5e9d7-103">`#endif` specifies the end of a conditional directive, which began with the [#if](./preprocessor-if.md) directive.</span></span> <span data-ttu-id="5e9d7-104">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="5e9d7-104">For example,</span></span>  
  
```csharp
#define DEBUG  
// ...  
#if DEBUG  
    Console.WriteLine("Debug version");  
#endif  
```  
  
## <a name="remarks"></a><span data-ttu-id="5e9d7-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5e9d7-105">Remarks</span></span>  
 <span data-ttu-id="5e9d7-106">Dyrektywa warunkowa, `#if` począwszy od dyrektywy, musi `#endif` zostać wyraźnie zakończona dyrektywą.</span><span class="sxs-lookup"><span data-stu-id="5e9d7-106">A conditional directive, beginning with a `#if` directive, must explicitly be terminated with a `#endif` directive.</span></span> <span data-ttu-id="5e9d7-107">Zobacz [#if](./preprocessor-if.md) przykład użycia `#endif`.</span><span class="sxs-lookup"><span data-stu-id="5e9d7-107">See [#if](./preprocessor-if.md) for an example of how to use `#endif`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e9d7-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5e9d7-108">See also</span></span>

- [<span data-ttu-id="5e9d7-109">Odwołanie do języka C#</span><span class="sxs-lookup"><span data-stu-id="5e9d7-109">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="5e9d7-110">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="5e9d7-110">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="5e9d7-111">Dyrektywy przedprocesorowe C#</span><span class="sxs-lookup"><span data-stu-id="5e9d7-111">C# Preprocessor Directives</span></span>](./index.md)
