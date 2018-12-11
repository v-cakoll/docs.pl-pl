---
title: '#undef - C# odwołania'
ms.custom: seodec18
ms.date: 06/30/2018
f1_keywords:
- '#undef'
helpviewer_keywords:
- '#undef directive [C#]'
ms.assetid: 686c92d2-7194-4be4-b2f4-80091712d513
ms.openlocfilehash: 5a3658c4e6bb32158e6f81c3ac5014fbedba0713
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53235770"
---
# <a name="undef-c-reference"></a><span data-ttu-id="1b9ea-102">#undef (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="1b9ea-102">#undef (C# Reference)</span></span>
<span data-ttu-id="1b9ea-103">Dyrektywa `#undef` umożliwia anulowanie definicji symbolu w taki sposób, że w przypadku użycia symbolu jako wyrażenia w dyrektywie [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) zostanie zwrócona wartość `false`.</span><span class="sxs-lookup"><span data-stu-id="1b9ea-103">`#undef` lets you undefine a symbol, such that, by using the symbol as the expression in a [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) directive, the expression will evaluate to `false`.</span></span>  
  
 <span data-ttu-id="1b9ea-104">Symbol może być zdefiniowana za pomocą [#define](../../../csharp/language-reference/preprocessor-directives/preprocessor-define.md) dyrektywy lub [— Zdefiniuj](../../../csharp/language-reference/compiler-options/define-compiler-option.md) — opcja kompilatora.</span><span class="sxs-lookup"><span data-stu-id="1b9ea-104">A symbol can be defined either with the [#define](../../../csharp/language-reference/preprocessor-directives/preprocessor-define.md) directive or the [-define](../../../csharp/language-reference/compiler-options/define-compiler-option.md) compiler option.</span></span> <span data-ttu-id="1b9ea-105">Dyrektywa `#undef` musi znajdować się w pliku przed użyciem jakichkolwiek instrukcji, które nie są również dyrektywami.</span><span class="sxs-lookup"><span data-stu-id="1b9ea-105">The `#undef` directive must appear in the file before you use any statements that are not also directives.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1b9ea-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="1b9ea-106">Example</span></span>  

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

<span data-ttu-id="1b9ea-107">**DEBUGOWANIE nie jest zdefiniowany.**</span><span class="sxs-lookup"><span data-stu-id="1b9ea-107">**DEBUG is not defined**</span></span>

## <a name="see-also"></a><span data-ttu-id="1b9ea-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1b9ea-108">See Also</span></span>

- [<span data-ttu-id="1b9ea-109">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="1b9ea-109">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="1b9ea-110">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="1b9ea-110">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="1b9ea-111">Dyrektywy preprocesora C#</span><span class="sxs-lookup"><span data-stu-id="1b9ea-111">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)
