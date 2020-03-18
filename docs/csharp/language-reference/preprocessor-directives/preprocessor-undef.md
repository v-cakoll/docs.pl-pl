---
title: '#undef — odwołanie do języka C#'
ms.date: 06/30/2018
f1_keywords:
- '#undef'
helpviewer_keywords:
- '#undef directive [C#]'
ms.assetid: 686c92d2-7194-4be4-b2f4-80091712d513
ms.openlocfilehash: 21923412aa178c3b86e94a54bd911130e48e4deb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712445"
---
# <a name="undef-c-reference"></a><span data-ttu-id="fde66-102">#undef (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="fde66-102">#undef (C# Reference)</span></span>
<span data-ttu-id="fde66-103">`#undef`umożliwia oddefiniowanie symbolu, tak aby za pomocą symbolu jako wyrażenia w `false` [#if](./preprocessor-if.md) dyrektywy wyrażenie będzie obliczać .</span><span class="sxs-lookup"><span data-stu-id="fde66-103">`#undef` lets you undefine a symbol, such that, by using the symbol as the expression in a [#if](./preprocessor-if.md) directive, the expression will evaluate to `false`.</span></span>  
  
 <span data-ttu-id="fde66-104">Symbol można zdefiniować za pomocą [#define](./preprocessor-define.md) dyrektywy lub [opcji -define](../compiler-options/define-compiler-option.md) kompilatora.</span><span class="sxs-lookup"><span data-stu-id="fde66-104">A symbol can be defined either with the [#define](./preprocessor-define.md) directive or the [-define](../compiler-options/define-compiler-option.md) compiler option.</span></span> <span data-ttu-id="fde66-105">Dyrektywa `#undef` musi pojawić się w pliku przed użyciem żadnych instrukcji, które nie są również dyrektywy.</span><span class="sxs-lookup"><span data-stu-id="fde66-105">The `#undef` directive must appear in the file before you use any statements that are not also directives.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fde66-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="fde66-106">Example</span></span>  

```csharp
// preprocessor_undef.cs  
// compile with: /d:DEBUG  
#undef DEBUG  
using System;  
class MyClass
{  
    static void Main()
    {  
#if DEBUG  
        Console.WriteLine("DEBUG is defined");  
#else  
        Console.WriteLine("DEBUG is not defined");  
#endif  
    }  
}  
```

<span data-ttu-id="fde66-107">**DEBUG nie jest zdefiniowany**</span><span class="sxs-lookup"><span data-stu-id="fde66-107">**DEBUG is not defined**</span></span>

## <a name="see-also"></a><span data-ttu-id="fde66-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fde66-108">See also</span></span>

- [<span data-ttu-id="fde66-109">Odwołanie do języka C#</span><span class="sxs-lookup"><span data-stu-id="fde66-109">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="fde66-110">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="fde66-110">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="fde66-111">Dyrektywy przedprocesorowe C#</span><span class="sxs-lookup"><span data-stu-id="fde66-111">C# Preprocessor Directives</span></span>](./index.md)
