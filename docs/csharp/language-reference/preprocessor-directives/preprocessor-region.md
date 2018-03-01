---
title: "#region (odwołanie w C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '#region'
helpviewer_keywords:
- '#region directive [C#]'
ms.assetid: 672c87d1-9771-4f64-ab3f-0ad3d4ffb2b4
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: cce4a8ac79c4687280e28618d8863d16cd193a3b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="region-c-reference"></a><span data-ttu-id="707fe-102">#region (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="707fe-102">#region (C# Reference)</span></span>
<span data-ttu-id="707fe-103">`#region`Pozwala określić blok kodu, który można rozwinąć lub zwinąć przy użyciu [zwijania](/visualstudio/ide/outlining) funkcji edytora kodu programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="707fe-103">`#region` lets you specify a block of code that you can expand or collapse when using the [outlining](/visualstudio/ide/outlining) feature of the Visual Studio Code Editor.</span></span> <span data-ttu-id="707fe-104">W plikach kodu dłużej jest wygodne można zwinąć lub ukrywanie jednego lub więcej regionów, dzięki czemu można skupić się w tej części pliku, który pracuje obecnie.</span><span class="sxs-lookup"><span data-stu-id="707fe-104">In longer code files, it is convenient to be able to collapse or hide one or more regions so that you can focus on the part of the file that you are currently working on.</span></span> <span data-ttu-id="707fe-105">Poniższy przykład przedstawia sposób definiowania regionu:</span><span class="sxs-lookup"><span data-stu-id="707fe-105">The following example shows how to define a region:</span></span>  
  
```csharp
#region MyClass definition  
public class MyClass   
{  
    static void Main()   
    {  
    }  
}  
#endregion  
```  
  
## <a name="remarks"></a><span data-ttu-id="707fe-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="707fe-106">Remarks</span></span>  
 <span data-ttu-id="707fe-107">A `#region` muszą kończyć bloku [#endregion](../../../csharp/language-reference/preprocessor-directives/preprocessor-endregion.md) dyrektywy.</span><span class="sxs-lookup"><span data-stu-id="707fe-107">A `#region` block must be terminated with a [#endregion](../../../csharp/language-reference/preprocessor-directives/preprocessor-endregion.md) directive.</span></span>  
  
 <span data-ttu-id="707fe-108">A `#region` bloku nie mogą nakładać się na [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) bloku.</span><span class="sxs-lookup"><span data-stu-id="707fe-108">A `#region` block cannot overlap with a [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) block.</span></span> <span data-ttu-id="707fe-109">Jednak `#region` bloku może być zagnieżdżona w `#if` bloku, a `#if` bloku może być zagnieżdżona w `#region` bloku.</span><span class="sxs-lookup"><span data-stu-id="707fe-109">However, a `#region` block can be nested in a `#if` block, and a `#if` block can be nested in a `#region` block.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="707fe-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="707fe-110">See Also</span></span>  
 [<span data-ttu-id="707fe-111">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="707fe-111">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="707fe-112">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="707fe-112">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="707fe-113">Dyrektywy preprocesora C#</span><span class="sxs-lookup"><span data-stu-id="707fe-113">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)
