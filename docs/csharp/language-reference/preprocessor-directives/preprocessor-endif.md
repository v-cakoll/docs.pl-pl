---
title: '#ENDIF - C# odwołania'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '#endif'
helpviewer_keywords:
- '#endif directive [C#]'
ms.assetid: 6a5fca55-5aee-441f-86f6-1c99fbe9ec05
ms.openlocfilehash: 13b43919b666dcc8c5adfc3490eaad73960547ae
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53243910"
---
# <a name="endif-c-reference"></a><span data-ttu-id="95a26-102">#endif (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="95a26-102">#endif (C# Reference)</span></span>
<span data-ttu-id="95a26-103">`#endif` Określa koniec warunkowego dyrektywy, który rozpoczął się [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) dyrektywy.</span><span class="sxs-lookup"><span data-stu-id="95a26-103">`#endif` specifies the end of a conditional directive, which began with the [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) directive.</span></span> <span data-ttu-id="95a26-104">Na przykład</span><span class="sxs-lookup"><span data-stu-id="95a26-104">For example,</span></span>  
  
```csharp
#define DEBUG  
// ...  
#if DEBUG  
    Console.WriteLine("Debug version");  
#endif  
```  
  
## <a name="remarks"></a><span data-ttu-id="95a26-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="95a26-105">Remarks</span></span>  
 <span data-ttu-id="95a26-106">Dyrektywy warunkowej, począwszy od `#if` dyrektywy, jawnie muszą być zakończone znakiem `#endif` dyrektywy.</span><span class="sxs-lookup"><span data-stu-id="95a26-106">A conditional directive, beginning with a `#if` directive, must explicitly be terminated with a `#endif` directive.</span></span> <span data-ttu-id="95a26-107">Aby zapoznać się z przykładem użycia dyrektywy [, zobacz ](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md)#if`#endif`.</span><span class="sxs-lookup"><span data-stu-id="95a26-107">See [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) for an example of how to use `#endif`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="95a26-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="95a26-108">See Also</span></span>

- [<span data-ttu-id="95a26-109">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="95a26-109">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="95a26-110">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="95a26-110">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="95a26-111">Dyrektywy preprocesora C#</span><span class="sxs-lookup"><span data-stu-id="95a26-111">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)
