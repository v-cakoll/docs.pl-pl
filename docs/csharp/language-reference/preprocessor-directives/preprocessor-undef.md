---
title: '#undef (odwołanie w C#)'
ms.date: 06/30/2018
f1_keywords:
- '#undef'
helpviewer_keywords:
- '#undef directive [C#]'
ms.assetid: 686c92d2-7194-4be4-b2f4-80091712d513
ms.openlocfilehash: 3957d58f61e51fab01618f5e1146be9cd0da58fd
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43661922"
---
# <a name="undef-c-reference"></a><span data-ttu-id="fdb3a-102">#undef (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="fdb3a-102">#undef (C# Reference)</span></span>
<span data-ttu-id="fdb3a-103">Dyrektywa `#undef` umożliwia anulowanie definicji symbolu w taki sposób, że w przypadku użycia symbolu jako wyrażenia w dyrektywie [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) zostanie zwrócona wartość `false`.</span><span class="sxs-lookup"><span data-stu-id="fdb3a-103">`#undef` lets you undefine a symbol, such that, by using the symbol as the expression in a [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) directive, the expression will evaluate to `false`.</span></span>  
  
 <span data-ttu-id="fdb3a-104">Symbol może być zdefiniowana za pomocą [#define](../../../csharp/language-reference/preprocessor-directives/preprocessor-define.md) dyrektywy lub [— Zdefiniuj](../../../csharp/language-reference/compiler-options/define-compiler-option.md) — opcja kompilatora.</span><span class="sxs-lookup"><span data-stu-id="fdb3a-104">A symbol can be defined either with the [#define](../../../csharp/language-reference/preprocessor-directives/preprocessor-define.md) directive or the [-define](../../../csharp/language-reference/compiler-options/define-compiler-option.md) compiler option.</span></span> <span data-ttu-id="fdb3a-105">Dyrektywa `#undef` musi znajdować się w pliku przed użyciem jakichkolwiek instrukcji, które nie są również dyrektywami.</span><span class="sxs-lookup"><span data-stu-id="fdb3a-105">The `#undef` directive must appear in the file before you use any statements that are not also directives.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fdb3a-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="fdb3a-106">Example</span></span>  

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

<span data-ttu-id="fdb3a-107">**DEBUGOWANIE nie jest zdefiniowany.**</span><span class="sxs-lookup"><span data-stu-id="fdb3a-107">**DEBUG is not defined**</span></span>

## <a name="see-also"></a><span data-ttu-id="fdb3a-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fdb3a-108">See Also</span></span>

- [<span data-ttu-id="fdb3a-109">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="fdb3a-109">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="fdb3a-110">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="fdb3a-110">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="fdb3a-111">Dyrektywy preprocesora C#</span><span class="sxs-lookup"><span data-stu-id="fdb3a-111">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)
