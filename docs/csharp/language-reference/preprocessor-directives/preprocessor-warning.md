---
title: '#Ostrzeżenie - C# odwołania'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '#warning'
helpviewer_keywords:
- '#warning directive [C#]'
ms.assetid: e6fb496d-bb8b-4018-baf6-5b60a0c8902b
ms.openlocfilehash: 55768a354b2841021607ed40b4ef87b9767edcad
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54620321"
---
# <a name="warning-c-reference"></a><span data-ttu-id="c6722-102">#warning (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="c6722-102">#warning (C# Reference)</span></span>
<span data-ttu-id="c6722-103">`#warning` Umożliwia wygenerowanie [CS1030](../../misc/cs1030.md) poziom jednego ostrzeżenia kompilatora z określonej lokalizacji w kodzie.</span><span class="sxs-lookup"><span data-stu-id="c6722-103">`#warning` lets you generate a [CS1030](../../misc/cs1030.md) level one compiler warning from a specific location in your code.</span></span> <span data-ttu-id="c6722-104">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="c6722-104">For example:</span></span>  
  
```csharp
#warning Deprecated code in this method.  
```  
  
## <a name="remarks"></a><span data-ttu-id="c6722-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="c6722-105">Remarks</span></span>
 <span data-ttu-id="c6722-106">Typowym zastosowaniem `#warning` jest dyrektywa warunkowa.</span><span class="sxs-lookup"><span data-stu-id="c6722-106">A common use of `#warning` is in a conditional directive.</span></span> <span data-ttu-id="c6722-107">Istnieje również możliwość wygenerowania błędu zdefiniowanego przez użytkownika przy użyciu dyrektywy [#error](../../../csharp/language-reference/preprocessor-directives/preprocessor-error.md).</span><span class="sxs-lookup"><span data-stu-id="c6722-107">It is also possible to generate a user-defined error with [#error](../../../csharp/language-reference/preprocessor-directives/preprocessor-error.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c6722-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="c6722-108">Example</span></span>  

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

## <a name="see-also"></a><span data-ttu-id="c6722-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c6722-109">See also</span></span>

- [<span data-ttu-id="c6722-110">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="c6722-110">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="c6722-111">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="c6722-111">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="c6722-112">Dyrektywy preprocesora C#</span><span class="sxs-lookup"><span data-stu-id="c6722-112">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)
