---
title: '#ostrzeżenie — odwołanie do języka C#'
ms.date: 07/20/2015
f1_keywords:
- '#warning'
helpviewer_keywords:
- '#warning directive [C#]'
ms.assetid: e6fb496d-bb8b-4018-baf6-5b60a0c8902b
ms.openlocfilehash: 38c3807a696599390667060d3bf374c68845fed0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75715067"
---
# <a name="warning-c-reference"></a><span data-ttu-id="bad57-102">#warning (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="bad57-102">#warning (C# Reference)</span></span>
<span data-ttu-id="bad57-103">`#warning`umożliwia wygenerowanie ostrzeżenia kompilatora poziomu [1 CS1030](../../misc/cs1030.md) z określonej lokalizacji w kodzie.</span><span class="sxs-lookup"><span data-stu-id="bad57-103">`#warning` lets you generate a [CS1030](../../misc/cs1030.md) level one compiler warning from a specific location in your code.</span></span> <span data-ttu-id="bad57-104">Przykład:</span><span class="sxs-lookup"><span data-stu-id="bad57-104">For example:</span></span>  
  
```csharp
#warning Deprecated code in this method.  
```  
  
## <a name="remarks"></a><span data-ttu-id="bad57-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bad57-105">Remarks</span></span>
 <span data-ttu-id="bad57-106">Powszechne stosowanie `#warning` jest w dyrektywie warunkowej.</span><span class="sxs-lookup"><span data-stu-id="bad57-106">A common use of `#warning` is in a conditional directive.</span></span> <span data-ttu-id="bad57-107">Istnieje również możliwość wygenerowania błędu zdefiniowanego przez użytkownika z [#error](./preprocessor-error.md).</span><span class="sxs-lookup"><span data-stu-id="bad57-107">It is also possible to generate a user-defined error with [#error](./preprocessor-error.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="bad57-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="bad57-108">Example</span></span>  

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

## <a name="see-also"></a><span data-ttu-id="bad57-109">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bad57-109">See also</span></span>

- [<span data-ttu-id="bad57-110">Odwołanie do języka C#</span><span class="sxs-lookup"><span data-stu-id="bad57-110">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="bad57-111">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="bad57-111">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="bad57-112">Dyrektywy przedprocesorowe C#</span><span class="sxs-lookup"><span data-stu-id="bad57-112">C# Preprocessor Directives</span></span>](./index.md)
