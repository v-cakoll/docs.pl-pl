---
title: '#undef - C# odwołania'
ms.custom: seodec18
ms.date: 06/30/2018
f1_keywords:
- '#undef'
helpviewer_keywords:
- '#undef directive [C#]'
ms.assetid: 686c92d2-7194-4be4-b2f4-80091712d513
ms.openlocfilehash: 0dedd1480dae15d2c04b47cee132ab3227098f56
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61688569"
---
# <a name="undef-c-reference"></a><span data-ttu-id="52dce-102">#undef (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="52dce-102">#undef (C# Reference)</span></span>
<span data-ttu-id="52dce-103">Dyrektywa `#undef` umożliwia anulowanie definicji symbolu w taki sposób, że w przypadku użycia symbolu jako wyrażenia w dyrektywie [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) zostanie zwrócona wartość `false`.</span><span class="sxs-lookup"><span data-stu-id="52dce-103">`#undef` lets you undefine a symbol, such that, by using the symbol as the expression in a [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) directive, the expression will evaluate to `false`.</span></span>  
  
 <span data-ttu-id="52dce-104">Symbol może być zdefiniowana za pomocą [#define](../../../csharp/language-reference/preprocessor-directives/preprocessor-define.md) dyrektywy lub [— Zdefiniuj](../../../csharp/language-reference/compiler-options/define-compiler-option.md) — opcja kompilatora.</span><span class="sxs-lookup"><span data-stu-id="52dce-104">A symbol can be defined either with the [#define](../../../csharp/language-reference/preprocessor-directives/preprocessor-define.md) directive or the [-define](../../../csharp/language-reference/compiler-options/define-compiler-option.md) compiler option.</span></span> <span data-ttu-id="52dce-105">Dyrektywa `#undef` musi znajdować się w pliku przed użyciem jakichkolwiek instrukcji, które nie są również dyrektywami.</span><span class="sxs-lookup"><span data-stu-id="52dce-105">The `#undef` directive must appear in the file before you use any statements that are not also directives.</span></span>  
  
## <a name="example"></a><span data-ttu-id="52dce-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="52dce-106">Example</span></span>  

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

<span data-ttu-id="52dce-107">**DEBUGOWANIE nie jest zdefiniowany.**</span><span class="sxs-lookup"><span data-stu-id="52dce-107">**DEBUG is not defined**</span></span>

## <a name="see-also"></a><span data-ttu-id="52dce-108">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="52dce-108">See also</span></span>

- [<span data-ttu-id="52dce-109">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="52dce-109">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="52dce-110">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="52dce-110">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="52dce-111">Dyrektywy preprocesora C#</span><span class="sxs-lookup"><span data-stu-id="52dce-111">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)
