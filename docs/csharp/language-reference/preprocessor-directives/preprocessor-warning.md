---
title: '#Ostrzeżenie- C# odwołanie'
ms.date: 07/20/2015
f1_keywords:
- '#warning'
helpviewer_keywords:
- '#warning directive [C#]'
ms.assetid: e6fb496d-bb8b-4018-baf6-5b60a0c8902b
ms.openlocfilehash: 38c3807a696599390667060d3bf374c68845fed0
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715067"
---
# <a name="warning-c-reference"></a><span data-ttu-id="76daf-102">#warning (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="76daf-102">#warning (C# Reference)</span></span>
<span data-ttu-id="76daf-103">`#warning` umożliwia wygenerowanie ostrzeżenia kompilatora o poziomie [CS1030](../../misc/cs1030.md) z określonej lokalizacji w kodzie.</span><span class="sxs-lookup"><span data-stu-id="76daf-103">`#warning` lets you generate a [CS1030](../../misc/cs1030.md) level one compiler warning from a specific location in your code.</span></span> <span data-ttu-id="76daf-104">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="76daf-104">For example:</span></span>  
  
```csharp
#warning Deprecated code in this method.  
```  
  
## <a name="remarks"></a><span data-ttu-id="76daf-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="76daf-105">Remarks</span></span>
 <span data-ttu-id="76daf-106">Typowym zastosowaniem `#warning` jest dyrektywa warunkowa.</span><span class="sxs-lookup"><span data-stu-id="76daf-106">A common use of `#warning` is in a conditional directive.</span></span> <span data-ttu-id="76daf-107">Istnieje również możliwość wygenerowania błędu zdefiniowanego przez użytkownika przy użyciu dyrektywy [#error](./preprocessor-error.md).</span><span class="sxs-lookup"><span data-stu-id="76daf-107">It is also possible to generate a user-defined error with [#error](./preprocessor-error.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="76daf-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="76daf-108">Example</span></span>  

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

## <a name="see-also"></a><span data-ttu-id="76daf-109">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="76daf-109">See also</span></span>

- [<span data-ttu-id="76daf-110">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="76daf-110">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="76daf-111">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="76daf-111">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="76daf-112">Dyrektywy preprocesora C#</span><span class="sxs-lookup"><span data-stu-id="76daf-112">C# Preprocessor Directives</span></span>](./index.md)
