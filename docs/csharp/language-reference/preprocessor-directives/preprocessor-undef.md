---
title: '#undef (odwołanie w C#)'
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '#undef'
helpviewer_keywords:
- '#undef directive [C#]'
ms.assetid: 686c92d2-7194-4be4-b2f4-80091712d513
caps.latest.revision: 12
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: e7a3c162c0ecb8bb39cc13a34dcd15fa3ce96ebb
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="undef-c-reference"></a><span data-ttu-id="cd450-102">#undef (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="cd450-102">#undef (C# Reference)</span></span>
<span data-ttu-id="cd450-103">`#undef`Umożliwia usuń symbol, taki sposób, że przy użyciu symbolu jako wyrażenie w [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) dyrektywy, wyrażenie, które będą oceniać do `false`.</span><span class="sxs-lookup"><span data-stu-id="cd450-103">`#undef` lets you undefine a symbol, such that, by using the symbol as the expression in a [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) directive, the expression will evaluate to `false`.</span></span>  
  
 <span data-ttu-id="cd450-104">Symbol może być zdefiniowany za pomocą [#define](../../../csharp/language-reference/preprocessor-directives/preprocessor-define.md) dyrektywy lub [/ define](../../../csharp/language-reference/compiler-options/define-compiler-option.md) — opcja kompilatora.</span><span class="sxs-lookup"><span data-stu-id="cd450-104">A symbol can be defined either with the [#define](../../../csharp/language-reference/preprocessor-directives/preprocessor-define.md) directive or the [/define](../../../csharp/language-reference/compiler-options/define-compiler-option.md) compiler option.</span></span> <span data-ttu-id="cd450-105">`#undef` Dyrektywa musi występować w pliku, aby korzystać z żadnych instrukcji, które nie są również dyrektywy.</span><span class="sxs-lookup"><span data-stu-id="cd450-105">The `#undef` directive must appear in the file before you use any statements that are not also directives.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cd450-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="cd450-106">Example</span></span>  
  
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
  
 <span data-ttu-id="cd450-107">**Nie zdefiniowano debugowania**</span><span class="sxs-lookup"><span data-stu-id="cd450-107">**DEBUG is not defined**</span></span>  
## <a name="see-also"></a><span data-ttu-id="cd450-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="cd450-108">See Also</span></span>  
 [<span data-ttu-id="cd450-109">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="cd450-109">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="cd450-110">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="cd450-110">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="cd450-111">Dyrektywy preprocesora C#</span><span class="sxs-lookup"><span data-stu-id="cd450-111">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)
