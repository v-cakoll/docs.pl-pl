---
title: '#endif — C# odwołanie'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '#endif'
helpviewer_keywords:
- '#endif directive [C#]'
ms.assetid: 6a5fca55-5aee-441f-86f6-1c99fbe9ec05
ms.openlocfilehash: 74205c836b4eeb2d8b17b907bb13708f3225df08
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69608570"
---
# <a name="endif-c-reference"></a><span data-ttu-id="f12c1-102">#endif (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="f12c1-102">#endif (C# Reference)</span></span>
<span data-ttu-id="f12c1-103">`#endif`Określa koniec dyrektywy warunkowej, która zaczyna się od dyrektywy [#if](./preprocessor-if.md) .</span><span class="sxs-lookup"><span data-stu-id="f12c1-103">`#endif` specifies the end of a conditional directive, which began with the [#if](./preprocessor-if.md) directive.</span></span> <span data-ttu-id="f12c1-104">Na przykład</span><span class="sxs-lookup"><span data-stu-id="f12c1-104">For example,</span></span>  
  
```csharp
#define DEBUG  
// ...  
#if DEBUG  
    Console.WriteLine("Debug version");  
#endif  
```  
  
## <a name="remarks"></a><span data-ttu-id="f12c1-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f12c1-105">Remarks</span></span>  
 <span data-ttu-id="f12c1-106">Dyrektywa warunkowa, rozpoczynająca się od `#if` dyrektywy, musi zostać jawnie zakończona `#endif` dyrektywą.</span><span class="sxs-lookup"><span data-stu-id="f12c1-106">A conditional directive, beginning with a `#if` directive, must explicitly be terminated with a `#endif` directive.</span></span> <span data-ttu-id="f12c1-107">Aby zapoznać się z przykładem użycia dyrektywy [, zobacz ](./preprocessor-if.md)#if`#endif`.</span><span class="sxs-lookup"><span data-stu-id="f12c1-107">See [#if](./preprocessor-if.md) for an example of how to use `#endif`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f12c1-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f12c1-108">See also</span></span>

- [<span data-ttu-id="f12c1-109">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="f12c1-109">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="f12c1-110">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="f12c1-110">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="f12c1-111">Dyrektywy preprocesora C#</span><span class="sxs-lookup"><span data-stu-id="f12c1-111">C# Preprocessor Directives</span></span>](./index.md)
