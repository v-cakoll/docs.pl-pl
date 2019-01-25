---
title: '#region — C# odwołania'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '#region'
helpviewer_keywords:
- '#region directive [C#]'
ms.assetid: 672c87d1-9771-4f64-ab3f-0ad3d4ffb2b4
ms.openlocfilehash: adaa58fc47da557a31270e99ff8a1dae3d0731bb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54724034"
---
# <a name="region-c-reference"></a><span data-ttu-id="a0675-102">#region (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="a0675-102">#region (C# Reference)</span></span>
<span data-ttu-id="a0675-103">Dyrektywa `#region` pozwala określić blok kodu, który można rozwinąć lub zwinąć przy użyciu funkcji [tworzenia konspektu](/visualstudio/ide/outlining) w edytorze kodu programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a0675-103">`#region` lets you specify a block of code that you can expand or collapse when using the [outlining](/visualstudio/ide/outlining) feature of the Visual Studio Code Editor.</span></span> <span data-ttu-id="a0675-104">W dłuższych plikach z kodem wygodniejsze jest zwinięcie lub ukrycie jednego lub kilku regionów, aby móc skupić się na tej części pliku, nad którą się obecnie pracuje.</span><span class="sxs-lookup"><span data-stu-id="a0675-104">In longer code files, it is convenient to be able to collapse or hide one or more regions so that you can focus on the part of the file that you are currently working on.</span></span> <span data-ttu-id="a0675-105">Poniższy przykład przedstawia sposób definiowania regionu:</span><span class="sxs-lookup"><span data-stu-id="a0675-105">The following example shows how to define a region:</span></span>  
  
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
  
## <a name="remarks"></a><span data-ttu-id="a0675-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a0675-106">Remarks</span></span>  
 <span data-ttu-id="a0675-107">Blok `#region` musi kończyć się dyrektywą [#endregion](../../../csharp/language-reference/preprocessor-directives/preprocessor-endregion.md).</span><span class="sxs-lookup"><span data-stu-id="a0675-107">A `#region` block must be terminated with a [#endregion](../../../csharp/language-reference/preprocessor-directives/preprocessor-endregion.md) directive.</span></span>  
  
 <span data-ttu-id="a0675-108">Blok `#region` nie może nakładać się na blok [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md).</span><span class="sxs-lookup"><span data-stu-id="a0675-108">A `#region` block cannot overlap with a [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) block.</span></span> <span data-ttu-id="a0675-109">Blok `#region` może natomiast być zagnieżdżony w bloku `#if`, a blok `#if` może być zagnieżdżony w bloku `#region`.</span><span class="sxs-lookup"><span data-stu-id="a0675-109">However, a `#region` block can be nested in a `#if` block, and a `#if` block can be nested in a `#region` block.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0675-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a0675-110">See also</span></span>

- [<span data-ttu-id="a0675-111">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="a0675-111">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="a0675-112">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="a0675-112">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="a0675-113">Dyrektywy preprocesora C#</span><span class="sxs-lookup"><span data-stu-id="a0675-113">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)
