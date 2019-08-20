---
title: '#undef — C# odwołanie'
ms.custom: seodec18
ms.date: 06/30/2018
f1_keywords:
- '#undef'
helpviewer_keywords:
- '#undef directive [C#]'
ms.assetid: 686c92d2-7194-4be4-b2f4-80091712d513
ms.openlocfilehash: fdf22e90be766e87e823a7f8cc27ea00c17d2bb5
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69605589"
---
# <a name="undef-c-reference"></a><span data-ttu-id="6ad3f-102">#undef (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="6ad3f-102">#undef (C# Reference)</span></span>
<span data-ttu-id="6ad3f-103">Dyrektywa `#undef` umożliwia anulowanie definicji symbolu w taki sposób, że w przypadku użycia symbolu jako wyrażenia w dyrektywie [#if](./preprocessor-if.md) zostanie zwrócona wartość `false`.</span><span class="sxs-lookup"><span data-stu-id="6ad3f-103">`#undef` lets you undefine a symbol, such that, by using the symbol as the expression in a [#if](./preprocessor-if.md) directive, the expression will evaluate to `false`.</span></span>  
  
 <span data-ttu-id="6ad3f-104">Symbol można zdefiniować za pomocą dyrektywy [#define](./preprocessor-define.md) lub opcji [-define](../compiler-options/define-compiler-option.md) kompilatora.</span><span class="sxs-lookup"><span data-stu-id="6ad3f-104">A symbol can be defined either with the [#define](./preprocessor-define.md) directive or the [-define](../compiler-options/define-compiler-option.md) compiler option.</span></span> <span data-ttu-id="6ad3f-105">Dyrektywa `#undef` musi znajdować się w pliku przed użyciem jakichkolwiek instrukcji, które nie są również dyrektywami.</span><span class="sxs-lookup"><span data-stu-id="6ad3f-105">The `#undef` directive must appear in the file before you use any statements that are not also directives.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6ad3f-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="6ad3f-106">Example</span></span>  

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

<span data-ttu-id="6ad3f-107">**Nie zdefiniowano debugowania**</span><span class="sxs-lookup"><span data-stu-id="6ad3f-107">**DEBUG is not defined**</span></span>

## <a name="see-also"></a><span data-ttu-id="6ad3f-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6ad3f-108">See also</span></span>

- [<span data-ttu-id="6ad3f-109">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="6ad3f-109">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="6ad3f-110">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="6ad3f-110">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="6ad3f-111">Dyrektywy preprocesora C#</span><span class="sxs-lookup"><span data-stu-id="6ad3f-111">C# Preprocessor Directives</span></span>](./index.md)
