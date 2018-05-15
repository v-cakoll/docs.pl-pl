---
title: '#Ostrzeżenie (odwołanie w C#)'
ms.date: 07/20/2015
f1_keywords:
- '#warning'
helpviewer_keywords:
- '#warning directive [C#]'
ms.assetid: e6fb496d-bb8b-4018-baf6-5b60a0c8902b
ms.openlocfilehash: c56458e0100c23450655e48b2abfb346e18e0bb8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="warning-c-reference"></a><span data-ttu-id="50555-102">#warning (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="50555-102">#warning (C# Reference)</span></span>
<span data-ttu-id="50555-103">`#warning` Umożliwia wygenerowanie ostrzeżenia poziomu pierwszego w określonej lokalizacji w kodzie.</span><span class="sxs-lookup"><span data-stu-id="50555-103">`#warning` lets you generate a level one warning from a specific location in your code.</span></span> <span data-ttu-id="50555-104">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="50555-104">For example:</span></span>  
  
```csharp
#warning Deprecated code in this method.  
```  
  
## <a name="remarks"></a><span data-ttu-id="50555-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="50555-105">Remarks</span></span>  
 <span data-ttu-id="50555-106">Typowym zastosowaniem `#warning` jest dyrektywa warunkowa.</span><span class="sxs-lookup"><span data-stu-id="50555-106">A common use of `#warning` is in a conditional directive.</span></span> <span data-ttu-id="50555-107">Istnieje również możliwość wygenerowania błędu zdefiniowanego przez użytkownika przy użyciu dyrektywy [#error](../../../csharp/language-reference/preprocessor-directives/preprocessor-error.md).</span><span class="sxs-lookup"><span data-stu-id="50555-107">It is also possible to generate a user-defined error with [#error](../../../csharp/language-reference/preprocessor-directives/preprocessor-error.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="50555-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="50555-108">Example</span></span>  
  
```csharp
// preprocessor_warning.cs  
// CS1030 expected  
#define DEBUG  
class MainClass   
{  
    static void Main()   
    {  
#if DEBUG  
#warning DEBUG is defined  
#endif  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="50555-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="50555-109">See Also</span></span>  
 [<span data-ttu-id="50555-110">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="50555-110">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="50555-111">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="50555-111">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="50555-112">Dyrektywy preprocesora C#</span><span class="sxs-lookup"><span data-stu-id="50555-112">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)
