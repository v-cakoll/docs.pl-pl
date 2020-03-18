---
title: '#region - Odwołanie do języka C#'
ms.date: 07/20/2015
f1_keywords:
- '#region'
helpviewer_keywords:
- '#region directive [C#]'
ms.assetid: 672c87d1-9771-4f64-ab3f-0ad3d4ffb2b4
ms.openlocfilehash: 48e8a6796c3b07b348fd988a9b8501ee496b8ad5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173396"
---
# <a name="region-c-reference"></a><span data-ttu-id="f9a5b-102">#region (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="f9a5b-102">#region (C# Reference)</span></span>
<span data-ttu-id="f9a5b-103">`#region`umożliwia określenie bloku kodu, który można rozwinąć lub zwinąć podczas korzystania z funkcji [konspektu](/visualstudio/ide/outlining) Edytora kodu programu Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="f9a5b-103">`#region` lets you specify a block of code that you can expand or collapse when using the [outlining](/visualstudio/ide/outlining) feature of the Visual Studio Code Editor.</span></span> <span data-ttu-id="f9a5b-104">W dłuższych plikach kodu wygodnie jest zwinąć lub ukryć jeden lub więcej regionów, dzięki czemu można skupić się na części pliku, nad którą aktualnie pracujesz.</span><span class="sxs-lookup"><span data-stu-id="f9a5b-104">In longer code files, it is convenient to be able to collapse or hide one or more regions so that you can focus on the part of the file that you are currently working on.</span></span> <span data-ttu-id="f9a5b-105">W poniższym przykładzie pokazano, jak zdefiniować region:</span><span class="sxs-lookup"><span data-stu-id="f9a5b-105">The following example shows how to define a region:</span></span>  
  
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
  
## <a name="remarks"></a><span data-ttu-id="f9a5b-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="f9a5b-106">Remarks</span></span>  
 <span data-ttu-id="f9a5b-107">Blok `#region` musi zostać zakończony dyrektywą [#endregion.](./preprocessor-endregion.md)</span><span class="sxs-lookup"><span data-stu-id="f9a5b-107">A `#region` block must be terminated with a [#endregion](./preprocessor-endregion.md) directive.</span></span>  
  
 <span data-ttu-id="f9a5b-108">Blok `#region` nie może nakładać się na blok [#if.](./preprocessor-if.md)</span><span class="sxs-lookup"><span data-stu-id="f9a5b-108">A `#region` block cannot overlap with a [#if](./preprocessor-if.md) block.</span></span> <span data-ttu-id="f9a5b-109">Jednak `#region` blok może być zagnieżdżone w `#if` bloku, a `#if` blok może być zagnieżdżone w `#region` bloku.</span><span class="sxs-lookup"><span data-stu-id="f9a5b-109">However, a `#region` block can be nested in a `#if` block, and a `#if` block can be nested in a `#region` block.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9a5b-110">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f9a5b-110">See also</span></span>

- [<span data-ttu-id="f9a5b-111">Odwołanie do języka C#</span><span class="sxs-lookup"><span data-stu-id="f9a5b-111">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="f9a5b-112">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="f9a5b-112">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="f9a5b-113">Dyrektywy przedprocesorowe C#</span><span class="sxs-lookup"><span data-stu-id="f9a5b-113">C# Preprocessor Directives</span></span>](./index.md)
