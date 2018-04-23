---
title: '#region (odwołanie w C#)'
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
caps.latest.revision: 12
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: cce4a8ac79c4687280e28618d8863d16cd193a3b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="region-c-reference"></a><span data-ttu-id="473f6-102">#region (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="473f6-102">#region (C# Reference)</span></span>
<span data-ttu-id="473f6-103">Dyrektywa `#region` pozwala określić blok kodu, który można rozwinąć lub zwinąć przy użyciu funkcji [tworzenia konspektu](/visualstudio/ide/outlining) w edytorze kodu programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="473f6-103">`#region` lets you specify a block of code that you can expand or collapse when using the [outlining](/visualstudio/ide/outlining) feature of the Visual Studio Code Editor.</span></span> <span data-ttu-id="473f6-104">W dłuższych plikach z kodem wygodniejsze jest zwinięcie lub ukrycie jednego lub kilku regionów, aby móc skupić się na tej części pliku, nad którą się obecnie pracuje.</span><span class="sxs-lookup"><span data-stu-id="473f6-104">In longer code files, it is convenient to be able to collapse or hide one or more regions so that you can focus on the part of the file that you are currently working on.</span></span> <span data-ttu-id="473f6-105">Poniższy przykład przedstawia sposób definiowania regionu:</span><span class="sxs-lookup"><span data-stu-id="473f6-105">The following example shows how to define a region:</span></span>  
  
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
  
## <a name="remarks"></a><span data-ttu-id="473f6-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="473f6-106">Remarks</span></span>  
 <span data-ttu-id="473f6-107">Blok `#region` musi kończyć się dyrektywą [#endregion](../../../csharp/language-reference/preprocessor-directives/preprocessor-endregion.md).</span><span class="sxs-lookup"><span data-stu-id="473f6-107">A `#region` block must be terminated with a [#endregion](../../../csharp/language-reference/preprocessor-directives/preprocessor-endregion.md) directive.</span></span>  
  
 <span data-ttu-id="473f6-108">Blok `#region` nie może nakładać się na blok [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md).</span><span class="sxs-lookup"><span data-stu-id="473f6-108">A `#region` block cannot overlap with a [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) block.</span></span> <span data-ttu-id="473f6-109">Blok `#region` może natomiast być zagnieżdżony w bloku `#if`, a blok `#if` może być zagnieżdżony w bloku `#region`.</span><span class="sxs-lookup"><span data-stu-id="473f6-109">However, a `#region` block can be nested in a `#if` block, and a `#if` block can be nested in a `#region` block.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="473f6-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="473f6-110">See Also</span></span>  
 [<span data-ttu-id="473f6-111">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="473f6-111">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="473f6-112">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="473f6-112">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="473f6-113">Dyrektywy preprocesora C#</span><span class="sxs-lookup"><span data-stu-id="473f6-113">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)
