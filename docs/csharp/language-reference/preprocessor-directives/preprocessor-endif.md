---
title: '#endif — C# odwołanie'
ms.date: 07/20/2015
f1_keywords:
- '#endif'
helpviewer_keywords:
- '#endif directive [C#]'
ms.assetid: 6a5fca55-5aee-441f-86f6-1c99fbe9ec05
ms.openlocfilehash: cc344a224e2308e843328b228dd5e2466d02069f
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712549"
---
# <a name="endif-c-reference"></a><span data-ttu-id="62120-102">#endif (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="62120-102">#endif (C# Reference)</span></span>
<span data-ttu-id="62120-103">`#endif` określa koniec dyrektywy warunkowej, która zaczyna się od dyrektywy [#if](./preprocessor-if.md) .</span><span class="sxs-lookup"><span data-stu-id="62120-103">`#endif` specifies the end of a conditional directive, which began with the [#if](./preprocessor-if.md) directive.</span></span> <span data-ttu-id="62120-104">Na przykład</span><span class="sxs-lookup"><span data-stu-id="62120-104">For example,</span></span>  
  
```csharp
#define DEBUG  
// ...  
#if DEBUG  
    Console.WriteLine("Debug version");  
#endif  
```  
  
## <a name="remarks"></a><span data-ttu-id="62120-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="62120-105">Remarks</span></span>  
 <span data-ttu-id="62120-106">Dyrektywa warunkowa, rozpoczynająca się od dyrektywy `#if`, musi zostać jawnie zakończona przy użyciu dyrektywy `#endif`.</span><span class="sxs-lookup"><span data-stu-id="62120-106">A conditional directive, beginning with a `#if` directive, must explicitly be terminated with a `#endif` directive.</span></span> <span data-ttu-id="62120-107">Aby zapoznać się z przykładem użycia dyrektywy [, zobacz ](./preprocessor-if.md)#if`#endif`.</span><span class="sxs-lookup"><span data-stu-id="62120-107">See [#if](./preprocessor-if.md) for an example of how to use `#endif`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="62120-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="62120-108">See also</span></span>

- [<span data-ttu-id="62120-109">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="62120-109">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="62120-110">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="62120-110">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="62120-111">Dyrektywy preprocesora C#</span><span class="sxs-lookup"><span data-stu-id="62120-111">C# Preprocessor Directives</span></span>](./index.md)
